---
title: Yönetilen kodda hata ayıklama | Microsoft Docs
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f6dd305b55e1ff7dd11b46f023906a8422b5504f
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72536051"
---
# <a name="debug-managed-code-c-visual-basic-f-ccli"></a>Yönetilen kodda hata ayıklamaC#(, Visual Basic F#, C++,/CLI)

Bu bölümde, yönetilen uygulamalar veya Visual Basic, C#ve C++/cligibi ortak dil çalışma zamanını hedefleyen dillerde yazılmış uygulamalar için yaygın hata ayıklama sorunları ve teknikleri ele alınmaktadır. Burada açıklanan teknikler, üst düzey tekniklerdir. [İlk olarak hata ayıklayıcıya bakın](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>Bu Bölümde

[Çıkış Penceresi \ tanılama iletileri](../debugger/diagnostic-messages-in-the-output-window.md)
**Çıkış** penceresine çalışma zamanı iletileri yazabileceğiniz <xref:System.Diagnostics.Debug> ve <xref:System.Diagnostics.Trace> sınıflarını açıklar. Bu sınıflar, belirtilen bir koşul başarısız olursa yürütmeyi kesintiye uğratmadan, yürütme ve bilgi çıkışının kesintiye girmeden bilgi çıktısını etkinleştiren çıkış yöntemlerini içerir.

[Yönetilen koddaki onaylamalar](../debugger/assertions-in-managed-code.md) \
@No__t_0 metotlarda bağımsız değişken olarak belirttiğiniz test koşullarını Yönetilen koddaki onayları açıklar. Buna ek olarak, bu konuda örnek kod, <xref:System.Diagnostics.Debug> ve <xref:System.Diagnostics.Trace> sınıf yöntemleri kullanma, kod hata ayıklama ve sürüm sürümlerinde, yan etkiler, onay bağımsız değişkenleri, onaylama davranışını özelleştirme ve yapılandırma dosyaları hakkında bilgi verilmektedir.

[Visual Basic \ durdur deyimleri](../debugger/stop-statements-in-visual-basic.md)
Kesme noktası ayarlamaya alternatif sağlayan `Stop` ifadesini açıklar. Örnek kod ayrıca, `Stop` ifadesiyle ve `End` ifadesiyle ve `Stop` ile `Assert` ifadesiyle karşılaştırmaların yanı sıra de sağlanır.

[Izlenecek yol: Windows formunda hata ayıklama](../debugger/walkthrough-debugging-a-windows-form.md) \
Windows formu oluşturmak ve bu formun hatalarını ayıklamak için adım adım yönergeler sağlar. Yönetilen bir Windows uygulamasının standart bir bileşeni olan Windows formu, en yaygın yönetilen uygulamalardan biridir. Bu izlenecek yol, C# Visual ve Visual Basic kullanır, ancak ile C++ Windows formu oluşturma teknikleri genellikle benzerdir.

[OnStart yönteminde hata ayıklama](../debugger/how-to-debug-the-onstart-method.md) \
, Yönetilen bir Windows hizmetinin `OnStart` yönteminde hata ayıklamanızı sağlayan kod örnekleri sağlar. Bir Windows hizmetinin `OnStart` yönteminde hata ayıklamak için, hizmetin benzetimini yapmak üzere birkaç satır kod eklemeniz gerekir.

[Karışık modda hata ayıklama](../debugger/debugging-mixed-mode-applications.md) \
Karışık modda uygulamalarda hata ayıklamayı açıklar. Bu, yerel kodu yönetilen kodla birleştiren tüm uygulamalar anlamına gelir.

[Hata: sistemde bir çekirdek hata ayıklayıcısı etkinleştirildiğinden hata ayıklama mümkün değil](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md) \
Hata ayıklama modunda başlatılan bir [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)], [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)] veya Windows NT sisteminde yönetilen kodda hata ayıklamaya çalıştığınızda oluşan hata iletisini açıklar.

[JIT iyileştirme ve hata ayıklama](../debugger/jit-optimization-and-debugging.md) \
Hata ayıklama sırasında JıT iyileştirmesinin etkilerini açıklar.

[LINQ ve DLıNQ \ hatalarını ayıklama](../debugger/debugging-linq.md)
LINQ sorgularının hatalarını ayıklama tekniklerini açıklar.

[Izlenecek yol: paralel uygulamada hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md) \
Paralel bir uygulamada hata ayıklamak için **paralel görevler** ve **Paralel Yığınlar** araç pencerelerinin nasıl kullanılacağını açıklar.

## <a name="related-sections"></a>İlgili Bölümler

[Intellitrace](../debugger/intellitrace.md) \
Uygulamanızın yürütme geçmişini IntelliTrace ile kaydederek daha hızlı ve kolay bir şekilde hata bulun. Kaydedilen olayları ve geri doğru ilerlemeden, uygulamanın durumunu zaman içinde önemli noktalarda incelemek için çağrılar yapın. Çok sayıda kesme noktası ayarlamadan veya uygulamanızı sık yeniden başlatarak kodunuzda hata ayıklayın. Visual Studio Enterprise gerektirir.

[Uygulamaları izleme ve işaretleme](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications) \
Uygulamasının, çalışırken uygulamanın yürütülmesini izlemenin ve izleme deyimlerinin kodunuzda stratejik konumlarda yerleştirilmesi için gereken bir yol olan izlemeyi açıklar. Bu konu ayrıca, izleme ve izleme, izleme anahtarları, izleme dinleyicileri, bir uygulamadaki kod izleme, uygulama koduna izleme deyimleri ekleme ve <xref:System.Diagnostics.Debug> ve <xref:System.Diagnostics.Trace> koşullu olarak derleme konularına yönelik bağlantılar sağlar.

[/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) \
İle C++yazılan koda <xref:System.Diagnostics.DebuggableAttribute> ekleyen bağlayıcı seçeneğini açıklar. Bu öznitelik, ile C++iliştirme gibi hata ayıklama özelliklerini kullanmak için gereklidir.

[Windows hizmet uygulamalarında hata ayıklama](/dotnet/framework/windows-services/how-to-debug-windows-service-applications) \
Windows hizmet uygulamalarında hata ayıklama, işleme ekleme, hizmetin `OnStart` yöntemindeki kodda hata ayıklama, ana yöntemdeki kod hata ayıklama, kesme noktaları ayarlama ve hizmetler Denetim Yöneticisi kullanma dahil olmak üzere önemli noktalar sağlar hizmetinizi başlatmak, durdurmak, duraklatmak ve devam ettirmek için.

[Hata ayıklama ve profil oluşturma](/dotnet/framework/debug-trace-profile/index) \
.NET uygulamalarında hata ayıklamayı ve yapılandırma gereksinimlerini açıklar.

[Betikte ve Web uygulamalarında hata ayıklama](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications) \
Betiklerin ve Web uygulamalarında hata ayıklarken karşılaşabileceğiniz yaygın hata ayıklama sorunlarını ve tekniklerini açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: tasarım zamanında özel Windows Forms Denetimlerinde hata ayıklama](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)
- [Hata Ayıklayıcısı Güvenliği](../debugger/debugger-security.md)
- [Visual Studio’da hata ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)