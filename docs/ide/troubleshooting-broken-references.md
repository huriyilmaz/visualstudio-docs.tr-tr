---
title: Bozuk başvurularda sorun giderme
description: Uygulamanın başvurulan bileşeni bulamaz durumda olması dışında bir nedenden kaynaklanabilen bozuk başvurularla ilgili sorunları gidermeyi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: fba8b77d946d501dfd444bc1a097c47b59b92f7f1c9d32163828bdca0f4a1367
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121386933"
---
# <a name="troubleshoot-broken-references"></a>Bozuk başvurularda sorun giderme

Uygulamanız bozuk bir başvuru kullanmaya çalışırsa bir özel durum hatası oluşturulur. Başvurulan bileşenin bulunamama durumu hatanın birincil tetikleyicisidir, ancak bir başvuru bozuk olarak değerlendirilen birkaç durum vardır. Bu örnekler aşağıdaki listede gösterilmiştir:

- Projenin başvuru yolu yanlış veya eksik.

- Başvurulan dosya silindi.

- Başvurulan dosya yeniden adlandırıldı.

- Ağ bağlantısı veya kimlik doğrulaması başarısız oldu.

- Başvuru, bilgisayarda yüklü olan bir COM bileşenine başvurur.

Aşağıdakiler bu sorunların çözümleridir.

> [!NOTE]
> Derlemeler içinde dosyalara proje dosyasında mutlak yollarla başvurur. Bu nedenle, çok düzeyli bir ortamda çalışan kullanıcıların yerel ortamında başvurulan bir derlemeyi eksik olması mümkündür. Bu hataları önlemek için, bu durumlarda projeden projeye başvurular eklemek daha iyidir. Daha fazla bilgi için [bkz. Derlemelerle programlama.](/dotnet/framework/app-domains/programming-with-assemblies)

## <a name="reference-path-is-incorrect"></a>Başvuru yolu yanlış

Projeler farklı bilgisayarlarda paylaşılıyorsa, bir bileşen her bilgisayarda farklı bir dizinde yer alıyorsa bazı başvurular bulunamıyor olabilir. Başvurular bileşen dosyasının adı altında depolanır (örneğin, *MyComponent*). Projeye bir başvuru ekleniyorsa, bileşen dosyasının klasör konumu (örneğin, *C:\MyComponents)* **ReferencePath** proje özelliğine eklenir.

Proje açıldığında, başvuru yolundaki dizinlere bakarak bu başvurulan bileşen dosyalarını bulmaya çalışır. Proje, bileşeni *D:\MyComponents* gibi farklı bir dizinde depolayan bir bilgisayarda açılırsa, başvuru bulunamaz ve **Görev Listesi.**

Bu sorunu çözmek için bozuk başvuru silinebilir ve ardından Başvuru Ekle iletişim **kutusunu kullanarak değiştirebilirsiniz.** Bir diğer çözüm  de projenin özellik sayfalarındaKi Başvuru Yolu öğesini kullanmak ve listede yer alan klasörleri doğru konumlara işaret etmek için değiştirmektir. Başvuru **Yolu özelliği** her bilgisayarda her kullanıcı için kalıcıdır. Bu nedenle, başvuru yolu değiştirerek projenin diğer kullanıcılarını etkilemez.

> [!TIP]
> Project proje başvurularda bu sorunlar yok. Bu nedenle, dosya başvuruları yerine bunları kullanabilirsiniz.

### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>Başvuru yolunu düzelterek bozuk proje başvurularını düzeltmek için

1. Bu **Çözüm Gezgini** proje düğümünü sağ tıklatın ve Özellikler'e **tıklayın.**

   Project **Tasarımcısı** görüntülenir.

1. Başvurular'ı Visual Basic **Başvurular sayfasını** seçin ve Başvuru Yolları **düğmesine** tıklayın. Başvuru **Yolları iletişim** kutusunda, Klasör alanına başvurabilirsiniz öğesini içeren klasörün yolunu  yazın ve ardından Klasör Ekle **düğmesine** tıklayın.

    C# kullanıyorsanız Başvuru Yolları **sayfasını** seçin. Klasör **alanına,** başvurabilirsiniz öğeyi içeren klasörün yolunu yazın ve ardından Klasör Ekle **düğmesine** tıklayın.

## <a name="referenced-file-has-been-deleted"></a>Başvurulan dosya silindi

Başvurulan dosya silinmiş olabilir ve sürücüde artık mevcut değildir.

### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>Sürücüde artık mevcut olan bir dosyanın bozuk proje başvurularını düzeltmek için

- Başvuru silin.

- Başvuru bilgisayarınızda başka bir konumda bulunuyorsa, bu konumdan okuyun.

## <a name="referenced-file-has-been-renamed"></a>Başvurulan dosya yeniden adlandırıldı

Başvurulan dosya yeniden adlandırıldı olabilir.

### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>Yeniden adlandırılmış bir dosyanın bozuk başvurularını düzeltmek için

- Başvuruyu silin ve yeniden adlandırılan dosyaya bir başvuru ekleyin.

- Başvuru bilgisayarınızda başka bir konumda bulunuyorsa, bu konumdan okumanız gerekir.

## <a name="network-connection-or-authentication-has-failed"></a>Ağ bağlantısı veya kimlik doğrulaması başarısız oldu

Erişilemeyen dosyalar için birçok olası neden olabilir: başarısız bir ağ bağlantısı veya başarısız kimlik doğrulaması, örneğin. Her nedenin benzersiz bir kurtarma aracı olabilir; Örneğin, gerekli kaynaklara erişim için yerel yöneticiyle iletişim kurmanız gerekebilir. Ancak, başvuru silmek ve bunu kullanılan kodu düzeltmek her zaman bir seçenektir.

## <a name="com-component-is-not-installed-on-computer"></a>COM bileşeni bilgisayarda yüklü değil

Kullanıcı bir COM bileşenine başvuru eklemişse ve ikinci kullanıcı bu bileşenin yüklü olduğu bir bilgisayarda kodu çalıştırmaya çalışırsa, ikinci kullanıcı başvuru bozuk hatası alır. Bileşeni ikinci bilgisayara yüklemek hatayı düzeltecek. Projeleriniz içindeki COM bileşenlerine yönelik başvuruları kullanma hakkında daha fazla bilgi için bkz. .NET Framework [com birlikte çalışabilirliği.](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications)

## <a name="see-also"></a>Ayrıca bkz.

- [Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)
