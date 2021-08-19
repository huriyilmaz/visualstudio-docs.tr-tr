---
title: Project Dosyalarına Veri | Microsoft Docs
description: Proje dosyasında alt türe özgü verileri kaydetmek ve almak için Yönetilen Paket Çerçevesi'nin sağladığı arabirimler hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 4e215954edfafa1463739431e0b422ae7521ab35
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158391"
---
# <a name="save-data-in-project-files"></a>Proje dosyalarına veri kaydetme
Proje alt türü, proje dosyasına alt türe özgü verileri kaydedip alabilir. Yönetilen Paket Çerçevesi (MPF), bu görevi gerçekleştirmek için iki arabirim sağlar:

- arabirimi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> proje dosyasının MSBuild  değerlerine erişmeye olanak sağlar. tarafından sağlanan yöntemler, kullanıcının derlemeyle ilgili verileri yüklemesi veya kaydetmesi gereken <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> her durumda herhangi bir kullanıcı tarafından çağrılabilirsiniz.

- , <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> derleme dışı ilgili verileri serbest biçimli XML'de kalıcı yapmak için kullanılır. tarafından sağlanan yöntemler, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> proje dosyasında derleme dışı ilgili verilerin kalıcı olması gereken her zaman tarafından [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çağrılır.

  Derleme ve derleme dışı ilgili verilerin kalıcı hale nasıl tutularak ilgili daha fazla bilgi için, bkz. [MSBuild proje dosyasında kalıcı hale.](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

## <a name="save-and-retrieve-build-related-data"></a>Derlemeyle ilgili verileri kaydetme ve alma

### <a name="to-save-a-build-related-data-in-the-project-file"></a>Derlemeyle ilgili verileri proje dosyasına kaydetmek için

- Proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> dosyasının tam yolunu kaydetmek için yöntemini çağırma.

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

### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Proje dosyasından derlemeyle ilgili verileri almak için

- Proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> dosyasının tam yolunu almak için yöntemini çağırma.

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

## <a name="save-and-retrieve-non-build-related-data"></a>Derlemeyle ilgili olmayan verileri kaydetme ve alma

### <a name="to-save-non-build-related-data-in-the-project-file"></a>Derlemeyle ilgili olmayan verileri proje dosyasına kaydetmek için

1. Bir <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> XML parçasının geçerli dosyasına son kaydedilmdan sonra değişip değişmediğini belirlemek için yöntemini kullanın.

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

2. XML <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> verilerini proje dosyasına kaydetmek için yöntemini uygulama.

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

### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Proje dosyasında derlemeyle ilgili olmayan verileri almak için

1. Proje uzantısı <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> özelliklerini ve diğer derlemeden bağımsız verileri başlatmak için yöntemini uygulama. Proje dosyasında xml yapılandırma verileri yoksa bu yöntem çağrılır.

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

2. Xml <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> verilerini proje dosyasından yüklemek için yöntemini uygulama.

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
> Bu konuda sağlanan tüm kod örnekleri, [VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples)örneklerinde daha büyük bir örneğin parçalarıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Verileri proje MSBuild kalıcı olarak kalıcı olarak kaydedin](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
