---
title: Verileri proje dosyalarına kaydetme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30d6652480318898e1528a6f2bb61b84621636d6
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848747"
---
# <a name="save-data-in-project-files"></a>Verileri proje dosyalarına Kaydet
Proje alt türü, proje dosyasında alt türe özgü verileri kaydedebilir ve alabilir. Yönetilen paket çerçevesi (MPF), bu görevi gerçekleştirmek için iki arabirim sağlar:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> arabirimi, proje dosyasının **MSBuild** bölümünde özellik değerlerine erişime izin verir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> tarafından verilen Yöntemler, kullanıcının derlemeden ilgili verileri yüklemesi veya kaydetmesi gerektiğinde herhangi bir kullanıcı tarafından çağrılabilir.

- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>, derleme olmayan ilgili verileri serbest biçimli XML 'de kalıcı hale getirmek için kullanılır. <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> tarafından verilen Yöntemler, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] derleme olmayan ilgili verileri proje dosyasında kalıcı hale getirmek için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tarafından çağrılır.

  Derlemeyi ve derleme dışı ilgili verileri kalıcı hale getirme hakkında daha fazla bilgi için bkz. [MSBuild proje dosyasında verileri kalıcı hale](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)getirme.

## <a name="save-and-retrieve-build-related-data"></a>Derleme ile ilgili verileri kaydetme ve alma

### <a name="to-save-a-build-related-data-in-the-project-file"></a>Derleme ile ilgili verileri proje dosyasına kaydetmek için

- Proje dosyasının tam yolunu kaydetmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> yöntemini çağırın.

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

### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Proje dosyasından derleme ile ilgili verileri almak için

- Proje dosyasının tam yolunu almak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> yöntemini çağırın.

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

## <a name="save-and-retrieve-non-build-related-data"></a>Derlemeden ilgili olmayan verileri kaydetme ve alma

### <a name="to-save-non-build-related-data-in-the-project-file"></a>Derleme olmayan ilgili verileri proje dosyasına kaydetmek için

1. Bir XML parçasının geçerli dosyasına son kaydedduğundan bu yana değiştirilip değiştirilmediğini anlamak için <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> yöntemini uygulayın.

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

2. XML verilerini proje dosyasına kaydetmek için <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> yöntemini uygulayın.

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

### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Derleme olmayan ilgili verileri proje dosyasında almak için

1. Proje uzantısı özelliklerini ve diğer derleme bağımsız verilerini başlatmak için <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> yöntemini uygulayın. Bu yöntem, proje dosyasında bir XML yapılandırma verisi yoksa çağrılır.

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

2. Proje dosyasından XML verilerini yüklemek için <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> yöntemini uygulayın.

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
> Bu konuda sağlanan tüm kod örnekleri, [VSSDK örneklerindeki](https://github.com/Microsoft/VSSDK-Extensibility-Samples)daha büyük bir örneğin parçalarından oluşur.

## <a name="see-also"></a>Ayrıca bkz.
- [MSBuild proje dosyasında verileri kalıcı hale getirme](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
