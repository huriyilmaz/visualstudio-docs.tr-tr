---
title: Özel Galeriler | Microsoft Docs
description: Visual Studio SDK'da geliştirdiğiniz denetimleri, şablonları ve araçları özel bir galeriye göndererek paylaşmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ae9a2683cf7f80b415b81a2f3f96d940ff62dc99
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102148"
---
# <a name="private-galleries"></a>Özel galeriler
Geliştirdiğiniz denetimleri, şablonları ve araçları, aşağıdaki gibi, kuruluş  için intranette özel bir galeriye göndererek paylaşabilirsiniz:

- İntranet üzerinde uygun şekilde yapılandırılmış merkezi bir konuma (depo) atom (RSS) akışı oluşturun. Daha fazla bilgi için, [bkz. How to: Create an Atom feed for a private gallery](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

- Özel *galeriyi açıklayan bir .pkgdef* dosyası dağıtabilirsiniz. Özel bir galeriyi aynı anda birçok bilgisayara bağlamak isteyen yöneticiler için bu yapılandırmayı öneririz.

## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Dosyalarda uzantılara ve güncelleştirmelere özel bir galeri Visual Studio
 Özel bir galeri kullanılabilir olduğunda, galeriyi uzantılar ve **güncelleştirmeler'e** Visual Studio.

 ![Uzantı Yöneticisi Ekle İletişim Kutusu](../extensibility/media/em_adddialog.png "EM_AddDialog")

### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Uzantılar ve Güncelleştirmeler'e özel galeri eklemek için

1. Menü çubuğunda Araçlar **Seçenekleri'ne**  >  **tıklayın.**

2. Ortam **düğümünde** Uzantılar ve **Güncelleştirmeler'i seçin.**

3. **Ekle** düğmesini seçin.

4. Ad **alanına** özel galeri için bir ad girin; örneğin, `My Gallery` .

5. URL **alanına** Atom akışı url'sini veya özel galeriyi SharePoint sitenin URL'sini girin.

    1. Ana bilgisayar özel galeriye bağlanan bir Atom akışı ise URL şu şekilde olur: `http://www.mywebsite/mygallery/atom.xml` .  Bu URL bir dosyaya veya ağ yoluna başvurur.

    2. Konak bir SharePoint sitesi ise URL şu şekilde olur: `http://mysharepoint/sites/mygallery/forms/AllItems.aspx` .

### <a name="manage-private-galleries"></a>Özel galerileri yönetme
 Bir yönetici, her bir bilgisayarda sistem kayıt defterini değiştirerek bir özel galeriyi aynı anda birkaç bilgisayarın kullanılabilir hale de olabilir. Bunu yapmak için, yeni kayıt defteri anahtarlarını ve değerlerini açıklayan bir *.pkgdef* dosyası oluşturun.  Bu dosyanın biçimi aşağıdaki gibidir.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 Daha fazla bilgi için, [bkz. How to: Manage a private gallery by using registry settings](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).

## <a name="install-extensions-from-a-private-gallery"></a>Özel galeriden uzantı yükleme
 Uzantılar ve Güncelleştirmeler'Visual Studio özel bir galeriden uzantılar için arama **ve yükleme yapabilirsiniz.** Aşağıdaki adımlar adlı özel bir galeri `My Gallery` kullanır.

 ![Özel Galeriyi Yükleyerek Uzantı Yöneticisi](../extensibility/media/em_.png "EM_")

### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Özel galeriden uzantıları aramak ve yüklemek için

1. Menü çubuğunda Araçlar Uzantıları ve  >  **Güncelleştirmeler'i seçin.**

2. Sol bölmede Çevrimiçi **Uzantılar'ı ve** ardından Galerim'i **seçin.**

3. Sağ bölmede bir uzantı seçin ve ardından İndir **düğmesini** seçin.

## <a name="update-extensions-from-a-private-gallery"></a>Özel galeriden uzantıları güncelleştirme
 Özel galeride Visual Studio sürümleri gönderildikten sonra, yüklemiş olduğu uzantıları güncelleştirebilirsiniz. Aşağıdaki adımlar adlı özel bir galeri `My Repository` kullanır.

 ![Uzantı Yöneticisi Özel Galeri Güncelleştirmesi](../extensibility/media/em_update.png "EM_Update")

### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Özel galeriden yüklü bir uzantıyı güncelleştirmek için

1. Menü çubuğunda Araçlar Uzantıları ve  >  **Güncelleştirmeler'i seçin.**

2. Sol bölmede Güncelleştirmeler'i **ve** ardından **Depom'ı seçin.**

3. Sağ bölmede bir uzantı seçin ve ardından Güncelleştir **düğmesini** seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio uzantıları bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md)
- [Visual Studio uzantıları gönder](../extensibility/shipping-visual-studio-extensions.md)
