---
title: Özel Galeriler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4056e4dedf06ffe86755bf946c77032d6f6782dd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702035"
---
# <a name="private-galleries"></a>Özel galeriler
Geliştirdiğiniz denetimleri, şablonları ve araçları kuruluşunuz için intranetteki özel bir *galeriye* göndererek aşağıdaki gibi paylaşabilirsiniz:

- İntranetinizde uygun şekilde yapılandırılmış merkezi bir konuma (depo) bir Atom (RSS) beslemesi oluşturun. Daha fazla bilgi için [bkz: Özel bir galeri için Atom akışı oluşturun.](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)

- Özel galeriyi açıklayan bir *.pkgdef* dosyası dağıtın. Özel bir galeriyi aynı anda birçok bilgisayara bağlamak isteyen yöneticiler için bu yapılandırmayı öneririz.

## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Visual Studio'daki uzantılara ve güncelleştirmelere özel bir galeri ekleme
 Özel bir galeri kullanılabilir olduğunda, Visual Studio'daki **Uzantılar ve Güncelleştirmeler'e** ekleyebilirsiniz.

 ![Uzantı Yöneticisi Ekle İletişim Kutusu](../extensibility/media/em_adddialog.png "EM_AddDialog")

### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Uzantılar ve Güncelleştirmeler için özel bir galeri eklemek için

1. Menü çubuğunda **Araç** > **Seçenekleri'ni**seçin.

2. **Ortam** düğümünde **Uzantılar ve Güncelleştirmeler'i**seçin.

3. **Ekle** düğmesini seçin.

4. **Ad** alanına, örneğin özel galeri için bir ad `My Gallery`girin.

5. **URL** alanına, özel galeriyi barındıran Atom akışı veya SharePoint sitesinin URL'sini girin.

    1. Ana bilgisayar özel galeriye bağlanan bir Atom akışıysa, URL http://www.mywebsite/mygallery/atom.xmlbuna benzer: .  Bu URL bir dosyaya veya ağ yoluna başvurabilir.

    2. Ana bilgisayar bir SharePoint sitesiyse, URL buna http://mysharepoint/sites/mygallery/forms/AllItems.aspxbenzer: .

### <a name="manage-private-galleries"></a>Özel galerileri yönetme
 Yönetici, her bilgisayardaki sistem kayıt defterini değiştirerek özel bir galeriyi aynı anda birden fazla bilgisayarın kullanımına açabilir. Bunu gerçekleştirmek için, yeni kayıt defteri anahtarlarını ve değerlerini açıklayan bir *.pkgdef* dosyası oluşturun.  Bu dosyanın biçimi aşağıdaki gibidir.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 Daha fazla bilgi için [bkz: Kayıt defteri ayarlarını kullanarak özel bir galeriyi yönetme.](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md)

## <a name="install-extensions-from-a-private-gallery"></a>Uzantıları özel bir galeriden yükleme
 **Uzantılar**ve Güncellemeler özel bir galeriden Visual Studio uzantılarını arayabilir ve yükleyebilirsiniz. Aşağıdaki adımlar adlandırılmış `My Gallery`özel bir galeri kullanır.

 ![Uzantı Yöneticisi Yükleme Özel Galeri](../extensibility/media/em_.png "EM_")

### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Özel bir galeriden uzantıları aramak ve yüklemek için

1. Menü çubuğunda, **Araç** > **Uzantıları ve Güncelleştirmeleri'ni**seçin.

2. Sol **bölmede, Çevrimiçi Uzantılar'ı**seçin ve ardından **Galerim'i**seçin.

3. Sağ bölmede bir uzantı seçin ve ardından **İndir** düğmesini seçin.

## <a name="update-extensions-from-a-private-gallery"></a>Uzantıları özel bir galeriden güncelleştirme
 Visual Studio uzantılarının yeni sürümleri özel galeride yayınlandığından, yüklediğiniz uzantıları güncelleştirebilirsiniz. Aşağıdaki adımlar adlandırılmış `My Repository`özel bir galeri kullanır.

 ![Uzantı Yöneticisi Özel Galeri Güncellemesi](../extensibility/media/em_update.png "EM_Update")

### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Özel bir galeriden yüklü bir uzantıyı güncelleştirmek için

1. Menü çubuğunda, **Araç** > **Uzantıları ve Güncelleştirmeleri'ni**seçin.

2. Sol bölmede **Güncelleştirmeler'i**seçin ve ardından **Depom'u**seçin.

3. Sağ bölmede bir uzantı seçin ve ardından **Güncelleştir** düğmesini seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio uzantıları bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md)
- [Gemi Görsel Stüdyo uzantıları](../extensibility/shipping-visual-studio-extensions.md)
