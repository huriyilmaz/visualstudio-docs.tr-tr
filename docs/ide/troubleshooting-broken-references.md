---
title: Bozuk başvurularda sorun giderme
ms.date: 03/21/2017
ms.topic: troubleshooting
helpviewer_keywords:
- C# projects, references
- Visual Basic projects, references
- troubleshooting references
- referencing files from projects
- referencing components, troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5116d2487ca9f53c460e1cae8f362f3ff1bcdf8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565922"
---
# <a name="troubleshoot-broken-references"></a>Bozuk başvurularda sorun giderme

Uygulamanız bozuk bir başvuru kullanmaya çalışırsa, bir özel durum hatası oluşturulur. Başvurulan bileşeni bulameme hatanın birincil tetikleyicisidir, ancak başvurunun bozuk olarak kabul edilebildiği birkaç durum vardır. Bu örnekler aşağıdaki listede gösterilir:

- Projenin başvuru yolu yanlış veya eksik.

- Başvurulan dosya silindi.

- Başvurulan dosyanın adı yeniden adlandırıldı.

- Ağ bağlantısı veya kimlik doğrulama başarısız oldu.

- Başvuru, bilgisayarda yüklü olmayan bir COM bileşenidir.

Aşağıdaki bu sorunların çareleri vardır.

> [!NOTE]
> Derlemelerde dosyalar, proje dosyasındaki mutlak yollar ile başvurulur. Bu nedenle, çok geliştiricili bir ortamda çalışan kullanıcıların yerel ortamlarında başvurulan bir derlemeeksik olması mümkündür. Bu hataları önlemek için, bu gibi durumlarda projeden projeye başvurular eklemek daha iyidir. Daha fazla bilgi için [derlemelerle Programlama'ya](/dotnet/framework/app-domains/programming-with-assemblies)bakın.

## <a name="reference-path-is-incorrect"></a>Başvuru yolu yanlış

Projeler farklı bilgisayarlarda paylaşılıyorsa, bileşen her bilgisayarda farklı bir dizinde bulunduğunda bazı başvurular bulunamayabilir. Başvurular bileşen dosyasının adı altında depolanır (örneğin, *MyComponent).* Bir projeye başvuru eklendiğinde, bileşen dosyasının klasör konumu (örneğin, *C:\MyComponents)* **ReferencePath** proje özelliğine eklenir.

Proje açıldığında, başvuru yolundaki dizinlere bakarak bu başvurulan bileşen dosyalarını bulmaya çalışır. Proje, bileşeni *D:\MyComponents*gibi farklı bir dizinde depolayan bir bilgisayarda açılırsa, başvuru bulunamıyor ve **Görev Listesinde**bir hata belirir.

Bu sorunu gidermek için bozuk başvuruyu silebilir ve **ardından Başvuru Ekle** iletişim kutusunu kullanarak değiştirebilirsiniz. Başka bir çözüm, projenin özellik **sayfalarındaki Başvuru Yolu** öğesini kullanmak ve listedeki klasörleri doğru konumları işaret etmek üzere değiştirmektir. **Başvuru Yolu** özelliği, her bilgisayardaki her kullanıcı için kalıcıdır. Bu nedenle, başvuru yolunuzu değiştirmek projenin diğer kullanıcılarını etkilemez.

> [!TIP]
> Projeden projeye başvurularda bu sorunlar yoktur. Bu nedenle, dosya başvuruları yerine bunları kullanın, eğer yapabilirseniz.

### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>Başvuru yolunu düzelterek bozuk proje başvurularını düzeltmek için

1. **Çözüm Gezgini'nde**proje düğümünüze sağ tıklayın ve **Özellikler'i**tıklatın.

   **Proje Tasarımcısı** görüntülenir.

1. Visual Basic kullanıyorsanız, **Başvurular** sayfasını seçin ve **Başvuru Yolları** düğmesini tıklatın. Başvuru **Yolları** iletişim kutusunda, **Klasör** alanında başvurmak istediğiniz öğeyi içeren klasörün yolunu yazın ve ardından **Klasör Ekle** düğmesini tıklatın.

    C# kullanıyorsanız, Başvuru **Yolları** sayfasını seçin. **Klasör** alanında, başvurmak istediğiniz öğeyi içeren klasörün yolunu yazın ve ardından **Klasör Ekle** düğmesini tıklatın.

## <a name="referenced-file-has-been-deleted"></a>Başvurulan dosya silindi

Başvurulan dosya silinmiş ve sürücüde artık bulunmamış olabilir.

### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>Sürücünüzde artık var olmayan bir dosya için bozuk proje başvurularını düzeltmek için

- Başvuruyu silin.

- Başvuru bilgisayarınızdaki başka bir konumda varsa, bu konumdan okuyun.

## <a name="referenced-file-has-been-renamed"></a>Başvurulan dosya nın adı yeniden adlandırıldı

Başvurulan dosyanın adı yeniden verilmiş olabilir.

### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>Yeniden adlandırılmış bir dosya için bozuk başvuruyonu düzeltmek için

- Başvuruyu silin ve yeniden adlandırılmış dosyaya bir başvuru ekleyin.

- Başvuru bilgisayarınızdaki başka bir konumda varsa, bu konumdan okumanız gerekir.

## <a name="network-connection-or-authentication-has-failed"></a>Ağ bağlantısı veya kimlik doğrulama başarısız oldu

Erişilemeyen dosyaların birçok olası nedeni olabilir: başarısız bir ağ bağlantısı veya başarısız bir kimlik doğrulama, örneğin. Her nedenin benzersiz bir kurtarma yolu olabilir; örneğin, gerekli kaynaklara erişmek için yerel yöneticiyle iletişim ebaşvurmanız gerekebilir. Ancak, başvurunun silmesi ve kullanılan kodun düzeltilmesi her zaman bir seçenektir.

## <a name="com-component-is-not-installed-on-computer"></a>COM bileşeni bilgisayarda yüklü değil

Bir kullanıcı com bileşenine bir başvuru eklediyse ve ikinci bir kullanıcı kodu bu bileşeni yüklü olmayan bir bilgisayarda çalıştırmaya çalışırsa, ikinci kullanıcı başvurunun bozulduklarına dair bir hata alır. Bileşeni ikinci bilgisayara yüklemek hatayı düzeltecektir. Projelerinizde COM bileşenlerine yapılan başvuruların nasıl kullanılacağı hakkında daha fazla bilgi için [,.NET Framework uygulamalarında COM birlikte çalışabilirliği'ne](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)
