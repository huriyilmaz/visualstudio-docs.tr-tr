---
title: Özel Galeriler | Microsoft Dokümanlar
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 895fbef5459de75c7ccdc6a090fc30ec27a030f9
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444927"
---
# <a name="private-galleries"></a>Özel Galeriler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Geliştirdiğiniz denetimleri, şablonları ve araçları kuruluşunuz için intranetteki özel bir *galeriye* göndererek aşağıdaki gibi paylaşabilirsiniz:  
  
- İntranetinizde uygun şekilde yapılandırılmış merkezi bir konuma (depo) bir Atom (RSS) beslemesi oluşturun. Daha fazla bilgi için [bkz: Özel Galeri için Atom Beslemesi Oluşturun.](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)  
  
- Özel galeriyi açıklayan bir .pkgdef dosyası dağıtın. Özel bir galeriyi aynı anda birçok bilgisayara bağlamak isteyen yöneticiler için bu yapılandırmayı öneririz.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Visual Studio'da Uzantılara ve Güncellemelere Özel Galeri Ekleme  
 Özel bir galeri kullanılabilir olduğunda, Visual Studio'daki **Uzantılar ve Güncelleştirmeler'e** ekleyebilirsiniz.  
  
 ![Uzantı Yöneticisi Ekle İletişim Kutusu](../extensibility/media/em-adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Uzantılar ve Güncelleştirmeler için özel bir galeri eklemek için  
  
1. Menü çubuğunda **Araçlar**, **Seçenekler'i**seçin.  
  
2. **Ortam** düğümünde **Uzantılar ve Güncelleştirmeler'i**seçin.  
  
3. **Ekle** düğmesini seçin.  
  
4. **Ad** alanına, örneğin özel galeri için bir ad `My Gallery`girin.  
  
5. **URL** alanına, özel galeriyi barındıran Atom akışı veya SharePoint sitesinin URL'sini girin.  
  
    1. Ana bilgisayar özel galeriye bağlanan bir Atom akışıysa, URL `http://www.mywebsite/mygallery/atom.xml`buna benzer: .  Bu URL bir dosyaya veya ağ yoluna başvurabilir.  
  
    2. Ana bilgisayar bir SharePoint sitesiyse, URL buna `http://mysharepoint/sites/mygallery/forms/AllItems.aspx`benzer: .  
  
### <a name="managing-private-galleries"></a>Özel Galerileri Yönetme  
 Yönetici, her bilgisayardaki sistem kayıt defterini değiştirerek özel bir galeriyi aynı anda birden fazla bilgisayarın kullanımına açabilir. Bunu gerçekleştirmek için, yeni kayıt defteri anahtarlarını ve değerlerini açıklayan bir .pkgdef dosyası oluşturun.  Bu dosyanın biçimi aşağıdaki gibidir.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Daha fazla bilgi için [bkz: Kayıt Defteri Ayarlarını Kullanarak Özel Galeriyi Yönetme](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="installing-extensions-from-a-private-gallery"></a>Özel Galeriden Uzantıyükleme  
 **Uzantılar**ve Güncellemeler özel bir galeriden Visual Studio uzantılarını arayabilir ve yükleyebilirsiniz. Aşağıdaki adımlar adlandırılmış `My Gallery`özel bir galeri kullanır.  
  
 ![Uzantı Yöneticisi Yükleme Özel Galeri](../extensibility/media/em.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Özel bir galeriden uzantıları aramak ve yüklemek için  
  
1. Menü çubuğunda **Araçlar,** **Uzantılar ve Güncelleştirmeler'i**seçin.  
  
2. Sol **bölmede, Çevrimiçi Uzantılar'ı**seçin ve ardından **Galerim'i**seçin.  
  
3. Sağ bölmede bir uzantı seçin ve ardından **İndir** düğmesini seçin.  
  
## <a name="updating-extensions-from-a-private-gallery"></a>Özel Galeri'den Uzantıları Güncelleme  
 Visual Studio uzantılarının yeni sürümleri özel galeride yayınlandığından, yüklediğiniz uzantıları güncelleştirebilirsiniz. Aşağıdaki adımlar adlandırılmış `My Repository`özel bir galeri kullanır.  
  
 ![Uzantı Yöneticisi Özel Galeri Güncellemesi](../extensibility/media/em-update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Özel bir galeriden yüklü bir uzantıyı güncelleştirmek için  
  
1. Menü çubuğunda **Araçlar,** **Uzantılar ve Güncelleştirmeler'i**seçin.  
  
2. Sol bölmede **Güncelleştirmeler'i**seçin ve ardından **Depom'u**seçin.  
  
3. Sağ bölmede bir uzantı seçin ve ardından **Güncelleştir** düğmesini seçin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Uzantılarını Bulma ve Kullanma](../ide/finding-and-using-visual-studio-extensions.md)   
 [Visual Studio Uzantıları Gönderme](../extensibility/shipping-visual-studio-extensions.md)
