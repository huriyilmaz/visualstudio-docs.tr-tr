---
title: Yönetilen kodda hata ayıklama | Microsoft Docs
description: Yönetilen uygulamalar için bkz. Visual Studio 'da ortak hata ayıklama sorunları ve teknikleri veya ortak dil çalışma zamanını hedefleyen dillerde yazılmış uygulamalar.
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
ms.workload:
- dotnet
ms.openlocfilehash: 1cac60b6b7187164780a67be24c7d8bdfb3b4eb2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872670"
---
# <a name="debug-managed-code-c-visual-basic-f-ccli"></a>Yönetilen kodda hata ayıklama (C#, Visual Basic, F #, C++/CLı)

Bu bölümde, yönetilen uygulamalar veya Visual Basic, C# ve C++/CLIGIBI ortak dil çalışma zamanını hedefleyen dillerde yazılmış uygulamalar için sık karşılaşılan hata ayıklama sorunları ve teknikleri ele alınmaktadır. Burada açıklanan teknikler, üst düzey tekniklerdir. [İlk olarak hata ayıklayıcıya bakın](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>Bu Bölümde

[Çıkış Penceresi tanılama Iletileri](../debugger/diagnostic-messages-in-the-output-window.md)\
<xref:System.Diagnostics.Debug>Ve <xref:System.Diagnostics.Trace> sınıflarını, çalışma zamanı iletilerini **Çıkış** penceresine yazabileceğiniz şekilde açıklar. Bu sınıflar, belirtilen bir koşul başarısız olursa yürütmeyi kesintiye uğratmadan, yürütme ve bilgi çıkışının kesintiye girmeden bilgi çıktısını etkinleştiren çıkış yöntemlerini içerir.

[Yönetilen koddaki Onaylamalar](../debugger/assertions-in-managed-code.md)\
Yöntemler için bağımsız değişken olarak belirttiğiniz test koşullarını Yönetilen koddaki onayları açıklar `Assert` . Buna ek olarak, bu konuda örnek kod, <xref:System.Diagnostics.Debug> ve sınıf yöntemleri hakkında bilgi, <xref:System.Diagnostics.Trace> kod hata ayıklama ve yayın sürümlerindeki konular, yan etkiler, onaylama bağımsız değişkenleri, onaylama davranışını özelleştirme ve yapılandırma dosyaları sağlanmaktadır.

[Visual Basic deyimlerini durdur](../debugger/stop-statements-in-visual-basic.md)\
`Stop`Kesme noktası ayarlamaya alternatif sağlayan ifadesini açıklar. Örnek kod ayrıca, ve deyimleri arasındaki karşılaştırmaların yanı sıra, `Stop` `End` `Stop` ve `Assert` deyimleriyle birlikte da sağlanır.

[İzlenecek yol: Windows formunda hata ayıklama](../debugger/walkthrough-debugging-a-windows-form.md)\
Windows formu oluşturmak ve bu formun hatalarını ayıklamak için adım adım yönergeler sağlar. Yönetilen bir Windows uygulamasının standart bir bileşeni olan Windows formu, en yaygın yönetilen uygulamalardan biridir. Bu izlenecek yol, Visual C# ve Visual Basic kullanır, ancak C++ ile Windows formu oluşturma teknikleri genellikle benzerdir.

[OnStart yönteminde hata ayıklama](../debugger/how-to-debug-the-onstart-method.md)\
Yönetilen bir Windows hizmeti yönteminde hata ayıklamanıza olanak tanımak için kod örnekleri sağlar `OnStart` . `OnStart`Bir Windows hizmeti yönteminde hata ayıklamak için, hizmetin benzetimini yapmak üzere birkaç satır kod eklemeniz gerekir.

[Karışık modda hata ayıklama](../debugger/debugging-mixed-mode-applications.md)\
Karışık modda uygulamalarda hata ayıklamayı açıklar. Bu, yerel kodu yönetilen kodla birleştiren tüm uygulamalar anlamına gelir.

[Hata: sistemde bir çekirdek hata ayıklayıcısı etkinleştirildiğinden hata ayıklama mümkün değil](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)\
Hata [!INCLUDE[win7](../debugger/includes/win7_md.md)] ayıklama modunda başlatılmış bir,,, [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)] veya Windows NT sisteminde yönetilen kodda hata ayıklamaya çalıştığınızda oluşan bir hata iletisi açıklanır.

[JıT Iyileştirme ve hata ayıklama](../debugger/jit-optimization-and-debugging.md)\
Hata ayıklama sırasında JıT iyileştirmesinin etkilerini açıklar.

[LINQ ve DLıNQ hatalarını ayıklama](../debugger/debugging-linq.md)\
LINQ sorgularının hatalarını ayıklama tekniklerini açıklar.

[İzlenecek yol: paralel uygulamada hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)\
Paralel bir uygulamada hata ayıklamak için **paralel görevler** ve **Paralel Yığınlar** araç pencerelerinin nasıl kullanılacağını açıklar.

## <a name="related-sections"></a>İlgili Bölümler

[IntelliTrace](../debugger/intellitrace.md)\
Uygulamanızın yürütme geçmişini IntelliTrace ile kaydederek daha hızlı ve kolay bir şekilde hata bulun. Kaydedilen olayları ve geri doğru ilerlemeden, uygulamanın durumunu zaman içinde önemli noktalarda incelemek için çağrılar yapın. Çok sayıda kesme noktası ayarlamadan veya uygulamanızı sık yeniden başlatarak kodunuzda hata ayıklayın. Visual Studio Enterprise gerektirir.

[Uygulamaları izleme ve Işaretleme](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)\
Uygulamasının, çalışırken uygulamanın yürütülmesini izlemenin ve izleme deyimlerinin kodunuzda stratejik konumlarda yerleştirilmesi için gereken bir yol olan izlemeyi açıklar. Bu konu ayrıca, izleme ve izleme, izleme anahtarları, izleme dinleyicileri, bir uygulamadaki kod izleme, uygulama koduna izleme deyimleri ekleme ve ile koşullu olarak derleme için bir giriş bağlantıları sağlar <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> .

[/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)\
<xref:System.Diagnostics.DebuggableAttribute>C++ ile yazılmış koda ekleyen bağlayıcı seçeneğini açıklar. Bu öznitelik, C++ ile iliştirme gibi hata ayıklama özelliklerini kullanmak için gereklidir.

[Windows hizmet uygulamalarında hata ayıklama](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)\
Windows hizmet uygulamalarında hata ayıklama, işleme ekleme, hizmetin yöntemindeki kodda hata ayıklama, ana yöntemdeki kodda hata ayıklama, `OnStart` ana yöntemdeki kod hata ayıklama, kesme noktası ayarlama ve hizmet Denetim Yöneticisi 'ni kullanarak hizmetinizi başlatma, durdurma, duraklatma ve devam etme gibi konuları sağlar.

[Hata ayıklama ve profil oluşturma](/dotnet/framework/debug-trace-profile/index)\
.NET uygulamalarında hata ayıklamayı ve yapılandırma gereksinimlerini açıklar.

[Betikte ve Web uygulamalarında hata ayıklama](how-to-enable-debugging-for-aspnet-applications.md)\
Betiklerin ve Web uygulamalarında hata ayıklarken karşılaşabileceğiniz yaygın hata ayıklama sorunlarını ve tekniklerini açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: tasarım zamanında özel Windows Forms Denetimlerinde hata ayıklama](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)
- [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)
- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)