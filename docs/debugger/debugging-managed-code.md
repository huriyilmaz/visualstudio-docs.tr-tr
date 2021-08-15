---
title: Yönetilen Kod Hata Ayıklama | Microsoft Docs
description: Yönetilen uygulamalar veya ortak dil çalışma zamanlarını Visual Studio dillerle yazılmış uygulamalar için genel hata ayıklama sorunlarına ve tekniklerine bakın.
ms.custom: SEO-VS-2020
ms.date: 09/23/2019
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging managed code
- debugging ASP.NET Web applications, managed code
- managed code, debugging
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- dotnet
ms.openlocfilehash: 0b4ff397996ac57d85ac52a338bdce6049e392dc725227c2021e384c81093931
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121240409"
---
# <a name="debug-managed-code-c-visual-basic-f-ccli"></a>Yönetilen Kodda Hata Ayıklama (C#, Visual Basic, F#, C++/CLI)

Bu bölümde yönetilen uygulamalara yönelik yaygın hata ayıklama sorunları ve teknikleri ya da Visual Basic, C# ve C++/CLI gibi ortak dil çalışma zamanlarını hedef alan dillerde yazılmış uygulamalar yer almaktadır. Burada açıklanan teknikler üst düzey tekniklerdir. [İlk olarak hata ayıklayıcısına bakın.](../debugger/debugger-feature-tour.md)

## <a name="in-this-section"></a>Bu Bölümde

[Tanılama İletileri Çıkış Penceresi](../debugger/diagnostic-messages-in-the-output-window.md)\
Çıkış <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> penceresine çalışma zamanı iletileri yazarak ve sınıflarını açıklar.  Bu sınıflar, yürütmeyi kesmeden bilgi çıkışını etkinleştiren çıkış yöntemlerini ve belirtilen bir koşul başarısız olduğunda yürütmeyi bozan bilgi çıkışını da içerir.

[Yönetilen Kodda Onaylar](../debugger/assertions-in-managed-code.md)\
Yöntemlerin bağımsız değişkenleri olarak belirttiğiniz koşulları test etmek için yönetilen kodda `Assert` onaylamaları açıklar. Ayrıca, bu konu örnek kod, kullanma ve sınıf yöntemleri hakkında bilgiler, Kodda Hata Ayıklama ve Yayın sürümlerinde dikkat edilmesi gerekenler, yan etkiler, onay bağımsız değişkenleri, onay davranışını özelleştirme ve yapılandırma <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> dosyaları sağlar.

[Visual Basic'de Stop Deyimleri](../debugger/stop-statements-in-visual-basic.md)\
Bir kesme `Stop` noktası ayarlamaya alternatif sağlayan deyimini açıklar. Örnek kod, deyimi ile deyimi arasındaki karşılaştırmaların yanı sıra ile deyimi `Stop` `End` arasında da `Stop` `Assert` sağlanır.

[adım adım kılavuz: Windows Form'da hata ayıklama](../debugger/walkthrough-debugging-a-windows-form.md)\
Form oluşturma ve bu formda hata ayıklama için Windows adım yönergeler verir. Yönetilen Windows standart bileşeni olan Windows Windows Form, en yaygın yönetilen uygulamalardan biri. Bu kılavuzda Visual C# ve Visual Basic, ancak C++ ile Windows oluşturma teknikleri genellikle benzerdir.

[OnStart Yönteminde Hata Ayıklama](../debugger/how-to-debug-the-onstart-method.md)\
Yönetilen bir hizmette yönetilen bir hizmette hata `OnStart` ayıklamasına olanak Windows sağlar. Windows `OnStart` hizmetinin Windows ayıklamak için, hizmetin benzetimini yapmak için birkaç kod satırı eklemeniz gerekir.

[Karma Mod Hata Ayıklama](../debugger/debugging-mixed-mode-applications.md)\
Karma mod uygulamalarında hata ayıklamayı tartışır. Bu, yerel kodu yönetilen kodla birleştiren herhangi bir uygulama anlamına gelir.

[Hata: Sistemde bir çekirdek hata ayıklayıcısı etkinleştirildiğinden hata ayıklama mümkün değil](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)\
, , , veya hata ayıklama modunda başlatan bir sistemde yönetilen kodun Windows NT hata ayıklamaya çalışırsanız oluşan bir [!INCLUDE[win7](../debugger/includes/win7_md.md)] [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] hata iletisini [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)] açıklar.

[JIT İyileştirme ve Hata Ayıklama](../debugger/jit-optimization-and-debugging.md)\
JIT iyileştirmenin hata ayıklama üzerindeki etkilerini açıklar.

[LINQ ve DLINQ'de Hata Ayıklama](../debugger/debugging-linq.md)\
LINQ sorgularında hata ayıklama tekniklerini ele almaktadır.

[Adım adım kılavuz: Paralel Uygulamada Hata Ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)\
Paralel uygulamada hata ayıklamak **için Paralel Görevler** ve Paralel **Yığınlar** araç pencerelerini kullanmayı açıklar.

## <a name="related-sections"></a>İlgili Bölümler

[ıntellitrace](../debugger/intellitrace.md)\
IntelliTrace ile uygulama yürütme geçmişini kaydederek hataları daha hızlı ve kolay bir şekilde bulun. Zaman içinde önemli noktalarda uygulama durumunu incelemek için kayıtlı olaylar ve çağrılar arasında geri ve ileri adım at. Çok sayıda kesme noktası ayarlamadan veya sık sık yeniden başlatmadan kodunuzun hata ayıklaması. Gerekli Visual Studio Enterprise.

[Uygulamaları İzleme ve İzleme](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)\
İzlemeyi açıklar. Bu, çalışırken uygulamanın yürütülmesini izlemenin bir yoludur ve izleme izlemesi sağlar. İzleme deyimlerini kodunuz içinde stratejik konumlara yerleştirmeyi içerir. Bu konu ayrıca izleme ve izleme, izleme anahtarları, izleme dinleyicileri, bir uygulama içinde izleme kodu izleme, uygulama koduna izleme deyimleri ekleme ve ve ile koşullu olarak derlemeye ilişkin bağlantılar <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> sağlar.

[/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)\
C++ ile yazılmış koda <xref:System.Diagnostics.DebuggableAttribute> ekleyen bir linker seçeneğini açıklar. Bu öznitelik, C++ ile ekleme gibi hata ayıklama özelliklerini kullanmak için gereklidir.

[Windows Hizmet Uygulamalarında Hata Ayıklama](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)\
Hizmetinizi başlatmak, durdurmak, duraklatmak ve devam etmek için Hizmet Denetim Yöneticisi'ni kullanmak gibi, Windows hizmet uygulamalarında hata ayıklama, işleme ekleme, hizmetin yönteminde kodda hata ayıklama ve Main yönteminde kodda hata ayıklama, kesme noktaları ayarlama ve Hizmet Denetimi Yöneticisi'ni kullanma gibi konuları `OnStart` sağlar.

[Hata Ayıklama ve Profil Oluşturma](/dotnet/framework/debug-trace-profile/index)\
.NET uygulamalarında hata ayıklamayı ve yapılandırma gereksinimlerini tartışmaktadır.

[Betik ve Web Uygulamalarında Hata Ayıklama](how-to-enable-debugging-for-aspnet-applications.md)\
Betik ve Web uygulamalarında hata ayıklarken karşılaşabilirsiniz yaygın hata ayıklama sorunlarını ve tekniklerini açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [Adım adım kılavuz: Tasarım Zamanında Windows Form Denetimlerinin Hata Ayıklaması](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)
- [Hata Ayıklayıcı Güvenliği](../debugger/debugger-security.md)
- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)