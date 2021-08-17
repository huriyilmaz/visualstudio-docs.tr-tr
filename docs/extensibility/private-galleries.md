---
title: Özel Galeriler | Microsoft Docs
description: Visual Studio SDK 'da geliştirerek yönettiğiniz denetimleri, şablonları ve araçları özel bir galeriye göndererek nasıl paylaşacağınızı öğrenin.
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
ms.openlocfilehash: b369996f59f91416cd0845e1b2b626e6dd1752d07935685a917589c382647c12
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121447856"
---
# <a name="private-galleries"></a>Özel galeriler
Yönettiğiniz denetimleri, şablonları ve araçları, kuruluşunuz için intranetteki *özel bir galeride* , aşağıdaki gibi paylaşabilirsiniz:

- İntranetinizdeki uygun şekilde ile yapılandırılmış bir merkezi konuma (depoya) bir atom (RSS) akışı oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: özel galeri Için Atom akışı oluşturma](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

- Özel galeriyi açıklayan bir *. pkgdef* dosyası dağıtın. Özel bir galeri 'yi aynı anda birçok bilgisayara bağlamak isteyen yöneticiler için bu yapılandırmayı öneririz.

## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Visual Studio içindeki uzantılara ve güncelleştirmelere özel galeri ekleme
 Özel Galeri kullanılabilir olduğunda, Visual Studio içindeki **uzantılara ve güncelleştirmelere** ekleyebilirsiniz.

 ![Uzantı Yöneticisi Iletişim kutusu Ekle](../extensibility/media/em_adddialog.png "EM_AddDialog")

### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Uzantılara ve güncelleştirmelere özel galeri eklemek için

1. Menü çubuğunda **Araçlar**  >  **Seçenekler**' i seçin.

2. **Ortam** düğümünde, **Uzantılar ve güncelleştirmeler**' i seçin.

3. **Ekle** düğmesini seçin.

4. **Ad** alanına, Özel Galeri için bir ad girin, örneğin, `My Gallery` .

5. **url** alanına, Atom akışı veya özel galeri barındıran SharePoint sitesinin url 'sini girin.

    1. Ana bilgisayar özel galeriye bağlanan bir atom akışsudur, URL şuna benzer: `http://www.mywebsite/mygallery/atom.xml` .  Bu URL, bir dosyaya veya bir ağ yoluna başvurabilir.

    2. ana bilgisayar bir SharePoint sitesi ise, URL şuna benzer: `http://mysharepoint/sites/mygallery/forms/AllItems.aspx` .

### <a name="manage-private-galleries"></a>Özel galerileri yönetme
 Yönetici, her bilgisayarda sistem kayıt defterini değiştirerek bir özel galeri 'yi aynı anda birçok bilgisayar için kullanılabilir hale getirir. Bunu gerçekleştirmek için, yeni kayıt defteri anahtarlarını ve bunların değerlerini açıklayan bir *. pkgdef* dosyası oluşturun.  Bu dosyanın biçimi aşağıdaki gibidir.

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

 Daha fazla bilgi için bkz. [nasıl yapılır: özel galeri 'yi kayıt defteri ayarlarını kullanarak yönetme](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).

## <a name="install-extensions-from-a-private-gallery"></a>Özel galerideki uzantıları yükler
 **uzantılar ve güncelleştirmeler**' de özel bir galeriden Visual Studio uzantıları arayabilir ve yükleyebilirsiniz. Aşağıdaki adımlarda adlı özel bir galeri kullanılır `My Gallery` .

 ![Uzantı Yöneticisi özel galeri yükleme](../extensibility/media/em_.png "EM_")

### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Özel bir galerideki uzantıları aramak ve yüklemek için

1. Menü çubuğunda **Araçlar**  >  **Uzantılar ve güncelleştirmeler**' i seçin.

2. Sol bölmede **çevrimiçi uzantılar**' ı seçin ve **galerim**' i seçin.

3. Sağ bölmede bir uzantı seçin ve ardından **İndir** düğmesini seçin.

## <a name="update-extensions-from-a-private-gallery"></a>Özel galerideki uzantıları güncelleştirme
 Visual Studio uzantılarının yeni sürümleri özel galeri 'de gönderildiğinde, yüklediğiniz uzantıları güncelleştirebilirsiniz. Aşağıdaki adımlarda adlı özel bir galeri kullanılır `My Repository` .

 ![Uzantı Yöneticisi özel galeri güncelleştirmesi](../extensibility/media/em_update.png "EM_Update")

### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Yüklü bir uzantıyı özel bir galeriden güncelleştirmek için

1. Menü çubuğunda **Araçlar**  >  **Uzantılar ve güncelleştirmeler**' i seçin.

2. Sol bölmede, **güncelleştirmeler**' i seçin ve sonra **deponuzu** seçin.

3. Sağ bölmede bir uzantı seçin ve ardından **Güncelleştir** düğmesini seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio uzantıları bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md)
- [Visual Studio uzantılarını gönder](../extensibility/shipping-visual-studio-extensions.md)
