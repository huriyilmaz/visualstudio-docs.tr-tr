---
title: Proje Dosyalarında Veri Kaydetme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5fd6cfaa450bc268665ae0f58109c99002da6152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701348"
---
# <a name="save-data-in-project-files"></a>Proje dosyalarına veri kaydetme
Proje alt türü, proje dosyasında alt türe özgü verileri kaydedebilir ve alabilir. Yönetilen Paket Çerçevesi (MPF) bu görevi gerçekleştirmek için iki arabirim sağlar:

- Arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> proje dosyasının **MSBuild** bölümünden özellik değerlerine erişmenizi sağlar. Kullanıcı nın <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> ilgili verileri yüklemesi veya kaydetmesi gerektiğinde, sağladığı yöntemler herhangi bir kullanıcı tarafından çağrılabilir.

- Yapı <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> dışı ilişkili verileri serbest biçimli XML'de sürdürmek için kullanılır. Tarafından <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> sağlanan yöntemler, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dosyasında yapı olmayan ilgili verileri devam etmesi gerektiğinde çağrılır.

  Yapı ve yapı oluşturmama ile ilgili verilerin nasıl devam edileceği hakkında daha fazla bilgi için [MSBuild proje dosyasındaki Devam verilerine](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)bakın.

## <a name="save-and-retrieve-build-related-data"></a>Yapı yla ilgili verileri kaydetme ve alma

### <a name="to-save-a-build-related-data-in-the-project-file"></a>Yapıyla ilgili verileri proje dosyasına kaydetmek için

- Proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> dosyasının tam yolunu kaydetmek için yöntemi arayın.

    ```
    private SpecializedProject project;
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;
    string newFullPath = GetNewFullPath();
    // Set a full path of the project file.
    ErrorHandler.ThrowOnFailure(projectStorage.SetPropertyValue(
        "MSBuildProjectDirectory",
        String.Empty,
        (uint)_PersistStorageType.PST_PROJECT_FILE, newFullPath));
    ```

### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Proje dosyasından yapı ile ilgili verileri almak için

- Proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> dosyasının tam yolunu almak için yöntemi arayın.

    ```
    private SpecializedProject project;
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;
    string fullPath;
    // Get a full path of the project file.
    ErrorHandler.ThrowOnFailure(projectStorage.GetPropertyValue(
        "MSBuildProjectDirectory",
        String.Empty,
        (uint)_PersistStorageType.PST_PROJECT_FILE, out fullPath));
    ```

## <a name="save-and-retrieve-non-build-related-data"></a>Yapı dışı ilişkili verileri kaydetme ve alma

### <a name="to-save-non-build-related-data-in-the-project-file"></a>Yapı dışı ilişkili verileri proje dosyasına kaydetmek için

1. Bir <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> XML parçasının geçerli dosyasına en son kaydedildiği için değişip değişmediğini belirlemek için yöntemi uygulayın.

    ```
    public int IsFragmentDirty(uint storage, out int pfDirty)
    {
        pfDirty = 0;
        switch (storage)
        {
            case (uint)_PersistStorageType.PST_PROJECT_FILE:
            {
                if (isDirty)
                    pfDirty |= 1;
                break;
            }
            case (uint)_PersistStorageType.PST_USER_FILE:
            {
                // We do not store anything in the user file.
                break;
            }
        }

        // Forward the call to inner flavor(s)
        if (pfDirty == 0 && innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).IsFragmentDirty(storage, out pfDirty);

        return VSConstants.S_OK;

    }
    ```

2. XML <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> verilerini proje dosyasına kaydetmek için yöntemi uygulayın.

    ```
    public int Save(ref Guid guidFlavor, uint storage, out string pbstrXMLFragment, int fClearDirty)
    {
        pbstrXMLFragment = null;

        if (IsMyFlavorGuid(ref guidFlavor))
        {
            switch (storage)
            {
                case (uint)_PersistStorageType.PST_PROJECT_FILE:
                {
                    // Create XML for our data.
                    XmlDocument doc = new XmlDocument();
                    XmlNode root = doc.CreateElement(this.GetType().Name);

                    XmlNode node = doc.CreateElement(targetsTag);
                    node.AppendChild(doc.CreateTextNode(this.TargetsToExecute));
                    root.AppendChild(node);

                    node = doc.CreateElement(updateTargetsTag);
                    node.AppendChild(doc.CreateTextNode(this.UpdateTargetList.ToString()));
                    root.AppendChild(node);

                    doc.AppendChild(root);
                    // Get XML fragment representing our data
                    pbstrXMLFragment = doc.InnerXml;

                    if (fClearDirty != 0)
                        isDirty = false;
                    break;
                }
                case (uint)_PersistStorageType.PST_USER_FILE:
                {
                    // We do not store anything in the user file.
                    break;
                }
            }
        }

        // Forward the call to inner flavor(s)
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).Save(ref guidFlavor, storage, out pbstrXMLFragment, fClearDirty);

        return VSConstants.S_OK;
    }
    ```

### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Proje dosyasında yapı yla ilgili olmayan verileri almak için

1. Proje <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> uzantısı özelliklerini ve diğer yapıbağımsız verileri başlatma yöntemini uygulayın. Proje dosyasında XML yapılandırma verisi yoksa bu yöntem çağrılır.

    ```
    public int InitNew(ref Guid guidFlavor, uint storage)
    {
        //Return,if it is our guid.
        if (IsMyFlavorGuid(ref guidFlavor))
            return VSConstants.S_OK;

        //Forward the call to inner flavor(s).
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).InitNew(ref guidFlavor, storage);

        return VSConstants.S_OK;
    ```

2. XML <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> verilerini proje dosyasından yüklemek için yöntemi uygulayın.

    ```
    public int Load(ref Guid guidFlavor, uint storage, string pszXMLFragment)
    {
        if (IsMyFlavorGuid(ref guidFlavor))
        {
            switch (storage)
            {
                case (uint)_PersistStorageType.PST_PROJECT_FILE:
                {
                    // Load our data from the XML fragment.
                    XmlDocument doc = new XmlDocument();
                    XmlNode node = doc.CreateElement(this.GetType().Name);
                    node.InnerXml = pszXMLFragment;
                    if (node == null
                        || node.FirstChild == null
                        || node.FirstChild.ChildNodes.Count == 0
                        || node.FirstChild.ChildNodes[0].Name != targetsTag)
                        break;
                    this.TargetsToExecute = node.FirstChild.ChildNodes[0].InnerText;

                    if (node.FirstChild.ChildNodes.Count <= 1
                        || node.FirstChild.ChildNodes[1].Name != updateTargetsTag)
                        break;
                    this.UpdateTargetList = bool.Parse(node.FirstChild.ChildNodes[1].InnerText);
                    break;
                }
                case (uint)_PersistStorageType.PST_USER_FILE:
                {
                    // We do not store anything in the user file.
                    break;
                }
            }
        }

        // Forward the call to inner flavor(s)
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).Load(ref guidFlavor, storage, pszXMLFragment);

        return VSConstants.S_OK;
    }
    ```

> [!NOTE]
> Bu konuda sağlanan tüm kod örnekleri [VSSDK örneklerinde](https://github.com/Microsoft/VSSDK-Extensibility-Samples)daha büyük bir örneğin parçalarıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [MSBuild proje dosyasındaki verileri devam ettir](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
