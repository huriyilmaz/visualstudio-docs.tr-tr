---
title: Bozuk başvurularda sorun giderme
description: Uygulamanın başvurulan bileşeni bulamaması dışında bir şeyin neden olabileceği hatalı başvuruların nasıl giderileceği hakkında bilgi edinin.
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
ms.workload:
- multiple
ms.openlocfilehash: 75e4d04641d593d8ced0c696cdca1efffd95e48d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971511"
---
# <a name="troubleshoot-broken-references"></a>Bozuk başvurularda sorun giderme

Uygulamanız bozuk bir başvuru kullanmayı denerse, bir özel durum hatası oluşturulur. Başvurulan bileşeni bulamama, hataya yönelik birincil tetikleyicidir, ancak başvurunun bozuk olarak kabul edileceği birkaç durum vardır. Bu örnekler aşağıdaki listede gösterilmiştir:

- Projenin başvuru yolu yanlış veya eksik.

- Başvurulan dosya silindi.

- Başvurulan dosya yeniden adlandırıldı.

- Ağ bağlantısı veya kimlik doğrulaması başarısız oldu.

- Başvuru, bilgisayarda yüklü olmayan bir COM bileşenidir.

Aşağıda bu sorunlara yönelik çözümler verilmiştir.

> [!NOTE]
> Derlemelerdeki dosyalara proje dosyasındaki mutlak yollarla başvurulur. Bu nedenle, birden çok geliştirici ortamında çalışan kullanıcıların yerel ortamlarında başvurulan bir derlemeyi eksik olması mümkündür. Bu hatalardan kaçınmak için, bu durumlarda projeden projeye başvurular eklemek daha iyidir. Daha fazla bilgi için bkz. [Derlemelerle programlama](/dotnet/framework/app-domains/programming-with-assemblies).

## <a name="reference-path-is-incorrect"></a>Başvuru yolu yanlış

Projeler farklı bilgisayarlarda paylaşılmışsa, bir bileşen her bilgisayarda farklı bir dizinde bulunuyorsa bazı başvurular bulunamamıştır. Başvurular, bileşen dosyasının adı altında depolanır (örneğin, *MyComponent*). Bir projeye başvuru eklendiğinde, bileşen dosyasının klasör konumu (örneğin, *C:\mycomponents*) **ReferencePath** proje özelliğine eklenir.

Proje açıldığında, başvuru yolundaki dizinlere bakarak bu başvurulan bileşen dosyalarını bulmaya çalışır. Proje, bileşeni *D:\mycomponents* gibi farklı bir dizinde depolayan bir bilgisayarda açılırsa, başvuru bulunamaz ve **görev listesi** bir hata görünür.

Bu sorunu gidermek için bozuk başvuruyu silebilir ve ardından **Başvuru Ekle** iletişim kutusunu kullanarak bunu değiştirebilirsiniz. Başka bir çözüm, projenin özellik sayfalarındaki **başvuru yolu** öğesini kullanmak ve listedeki klasörleri doğru konumlara işaret etmek için değiştirmektir. Her bilgisayardaki her bir kullanıcı için **başvuru yolu** özelliği kalıcıdır. Bu nedenle, başvuru yolunuzda değişiklik yapmak projenin diğer kullanıcılarını etkilemez.

> [!TIP]
> Projeden projeye başvurular bu sorunlara sahip değildir. Bu nedenle, mümkünse dosya başvuruları yerine bunları kullanın.

### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>Başvuru yolunu düzelterek bozuk bir proje başvurusunu düzeltmek için

1. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Özellikler**' e tıklayın.

   **Proje Tasarımcısı** görüntülenir.

1. Visual Basic kullanıyorsanız, **Başvurular** sayfasını seçin ve **başvuru yolları** düğmesine tıklayın. **Başvuru yolları** iletişim kutusunda, **klasör** alanına başvurmak istediğiniz öğeyi içeren klasörün yolunu yazın ve ardından **Klasör Ekle** düğmesine tıklayın.

    C# kullanıyorsanız, **başvuru yolları** sayfasını seçin. **Klasör** alanına, başvurmak istediğiniz öğeyi içeren klasörün yolunu yazın ve ardından **Klasör Ekle** düğmesine tıklayın.

## <a name="referenced-file-has-been-deleted"></a>Başvurulan dosya silindi

Başvurulan dosya silinmiş ve sürücüde artık yok olabilir.

### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>Sürücünüzde artık mevcut olmayan bir dosya için bozuk bir proje başvurusunu onarmak için

- Başvuruyu silin.

- Başvuru bilgisayarınızdaki başka bir konumda varsa, bu konumdan okuyun.

## <a name="referenced-file-has-been-renamed"></a>Başvurulan dosya yeniden adlandırıldı

Başvurulan dosya yeniden adlandırılmış olabilir.

### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>Yeniden adlandırılmış bir dosya için bozuk bir başvuruyu onarmak için

- Başvuruyu silin ve yeniden adlandırılan dosyaya bir başvuru ekleyin.

- Başvuru bilgisayarınızda başka bir konumda varsa, bu konumdan ' de okumanız gerekir.

## <a name="network-connection-or-authentication-has-failed"></a>Ağ bağlantısı veya kimlik doğrulaması başarısız oldu

Erişilemeyen dosyaların birçok nedeni olabilir: Örneğin, başarısız bir ağ bağlantısı veya başarısız bir kimlik doğrulama. Her nedenin benzersiz bir kurtarma yöntemi olabilir; Örneğin, gerekli kaynaklara erişmek için yerel yöneticiye başvurmanız gerekebilir. Ancak, başvuruyu silmek ve kullanan kodu düzeltmek her zaman bir seçenektir.

## <a name="com-component-is-not-installed-on-computer"></a>COM bileşeni bilgisayarda yüklü değil

Bir Kullanıcı bir COM bileşenine başvuru eklediyseniz ve ikinci bir Kullanıcı bu bileşenin yüklü olmadığı bir bilgisayarda kodu çalıştırmayı denediğinde ikinci Kullanıcı başvurunun bozulduğunu belirten bir hata alır. Bileşenin ikinci bilgisayara yüklenmesi hatayı düzeltecektir. Projelerinizde COM bileşenlerine başvuruların nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [.NET Framework uygulamalarda com birlikte çalışabilirliği](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications).

## <a name="see-also"></a>Ayrıca bkz.

- [Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)
