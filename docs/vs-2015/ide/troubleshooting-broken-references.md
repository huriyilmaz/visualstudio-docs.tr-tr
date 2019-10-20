---
title: Hatalı başvuruların sorunlarını giderme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- Visual C# projects, references
- Visual Basic projects, references
- troubleshooting references
- referencing files from projects
- referencing components, troubleshooting
ms.assetid: 00a9ade9-652e-40de-8ada-85f63cd183ee
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1dd1312fc5728fbb68994fb6e70e253fa19172e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654794"
---
# <a name="troubleshooting-broken-references"></a>Bozuk Başvurularda Sorun Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanız bozuk bir başvuru kullanmayı denerse, bir özel durum hatası oluşturulur. Başvurulan bileşeni bulamama, hataya yönelik birincil tetikleyicidir, ancak başvurunun bozuk olarak kabul edileceği birkaç durum vardır. Bu örnekler aşağıdaki listede gösterilmiştir:

- Projenin başvuru yolu yanlış veya eksik.

- Başvurulan dosya silindi.

- Başvurulan dosya yeniden adlandırıldı.

- Ağ bağlantısı veya kimlik doğrulaması başarısız oldu.

- Başvuru, bilgisayarda yüklü olmayan bir COM bileşenidir.

  Aşağıda bu sorunlara yönelik çözümler verilmiştir.

> [!NOTE]
> Derlemelerdeki dosyalara proje dosyasındaki mutlak yollarla başvurulur. Bu nedenle, birden çok geliştirici ortamında çalışan kullanıcıların yerel ortamlarında başvurulan bir derlemeyi eksik olması mümkündür. Bu hatalardan kaçınmak için, bu durumlarda projeden projeye başvurular eklemek daha iyidir. Daha fazla bilgi için bkz. [nib nasıl yapılır: Başvuru Ekle Iletişim kutusunu](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) ve [Derlemelerle programlama](https://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)kullanarak başvuru ekleme veya kaldırma.

## <a name="reference-path-is-incorrect"></a>Başvuru yolu yanlış
 Projeler farklı bilgisayarlarda paylaşılmışsa, bir bileşen her bilgisayarda farklı bir dizinde bulunuyorsa bazı başvurular bulunamamıştır. Başvurular, bileşen dosyasının adı altında depolanır (örneğin, MyComponent). Bir projeye başvuru eklendiğinde, bileşen dosyasının klasör konumu (örneğin, C:\MyComponents \\) **ReferencePath** proje özelliğine eklenir.

 Proje açıldığında, başvuru yolundaki dizinlere bakarak bu başvurulan bileşen dosyalarını bulmaya çalışır. Proje, bileşeni D:\MyComponents \\ gibi farklı bir dizinde depolayan bir bilgisayarda açılırsa, başvuru bulunamamıştır ve Görev Listesi bir hata görünür.

 Bu sorunu gidermek için bozuk başvuruyu silebilir ve ardından Başvuru Ekle iletişim kutusunu kullanarak bunu değiştirebilirsiniz. Başka bir çözüm, projenin özellik sayfalarındaki **başvuru yolu** öğesini kullanmak ve listedeki klasörleri doğru konumlara işaret etmek için değiştirmektir. Her bilgisayardaki her bir kullanıcı için **başvuru yolu** özelliği kalıcıdır. Bu nedenle, başvuru yolunuzda değişiklik yapmak projenin diğer kullanıcılarını etkilemez.

> [!TIP]
> Projeden projeye başvurular bu sorunlara sahip değildir. Bu nedenle, mümkünse dosya başvuruları yerine bunları kullanın.

#### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>Başvuru yolunu düzelterek bozuk bir proje başvurusunu düzeltmek için

1. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Özellikler**' e tıklayın.

2. **Proje Tasarımcısı** görüntülenir.

3. Visual Basic kullanıyorsanız, **Başvurular** sayfasını seçin ve **başvuru yolları** düğmesine tıklayın. **Başvuru yolları** iletişim kutusunda, **klasör** alanına başvurmak istediğiniz öğeyi içeren klasörün yolunu yazın ve ardından **Klasör Ekle** düğmesine tıklayın.

     veya

     Görsel C#kullanıyorsanız, **başvuru yolları** sayfasını seçin. **Klasör** alanına, başvurmak istediğiniz öğeyi içeren klasörün yolunu yazın ve ardından **Klasör Ekle** düğmesine tıklayın.

## <a name="referenced-file-has-been-deleted"></a>Başvurulan dosya silindi
 Başvurulan dosya silinmiş ve sürücüde artık yok olabilir.

#### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>Sürücünüzde artık mevcut olmayan bir dosya için bozuk bir proje başvurusunu onarmak için

- Başvuruyu silin.

- Başvuru bilgisayarınızdaki başka bir konumda varsa, bu konumdan okuyun.

- Daha fazla bilgi için bkz. [nib nasıl yapılır: Başvuru Ekle Iletişim kutusunu kullanarak başvuru ekleme veya kaldırma](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

## <a name="referenced-file-has-been-renamed"></a>Başvurulan dosya yeniden adlandırıldı
 Başvurulan dosya yeniden adlandırılmış olabilir.

#### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>Yeniden adlandırılmış bir dosya için bozuk bir başvuruyu onarmak için

- Başvuruyu silin ve yeniden adlandırılan dosyaya bir başvuru ekleyin.

- Başvuru bilgisayarınızda başka bir konumda varsa, bu konumdan ' de okumanız gerekir. Daha fazla bilgi için bkz. [nib nasıl yapılır: Başvuru Ekle Iletişim kutusunu kullanarak başvuru ekleme veya kaldırma](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

## <a name="network-connection-or-authentication-has-failed"></a>Ağ bağlantısı veya kimlik doğrulaması başarısız oldu
 Erişilemeyen dosyaların birçok nedeni olabilir: Örneğin, başarısız bir ağ bağlantısı veya başarısız bir kimlik doğrulama. Her nedenin benzersiz bir kurtarma yöntemi olabilir; Örneğin, gerekli kaynaklara erişmek için yerel yöneticiye başvurmanız gerekebilir. Ancak, başvuruyu silmek ve kullanan kodu düzeltmek her zaman bir seçenektir. Daha fazla bilgi için bkz. [nib nasıl yapılır: Başvuru Ekle Iletişim kutusunu kullanarak başvuru ekleme veya kaldırma](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

## <a name="com-component-is-not-installed-on-computer"></a>COM bileşeni bilgisayarda yüklü değil
 Bir Kullanıcı bir COM bileşenine başvuru eklediyseniz ve ikinci bir Kullanıcı bu bileşenin yüklü olmadığı bir bilgisayarda kodu çalıştırmayı denediğinde ikinci Kullanıcı başvurunun bozulduğunu belirten bir hata alır. Bileşenin ikinci bilgisayara yüklenmesi hatayı düzeltecektir. Projelerinizde COM bileşenlerine başvuruların nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [.NET Framework uygulamalarda com birlikte çalışabilirliği](https://msdn.microsoft.com/library/f5a72143-c268-4dff-a019-974ad940e17d).

## <a name="see-also"></a>Ayrıca Bkz.
 [Proje Tasarımcısı](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7) [başvuruları sayfasına giriş, proje Tasarımcısı (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md) [nib nasıl yapılır: Başvuru Ekle iletişim kutusunu kullanarak başvuru ekleme veya kaldırma](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
