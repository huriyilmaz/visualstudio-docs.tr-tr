---
title: Yönetilen kodda hata ayıklama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging managed code
- debugging ASP.NET Web applications, managed code
- managed code, debugging
ms.assetid: fa3aff01-c271-4aa7-b5b1-def560471c84
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 39076459f684aafce4e800ecad6341d120aac480
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691435"
---
# <a name="debugging-managed-code"></a>Yönetilen Kodda Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde, yönetilen uygulamalar veya Visual Basic, C# ve C++ gibi ortak dil çalışma zamanını hedefleyen dillerde yazılmış uygulamalar için yaygın hata ayıklama sorunları ve teknikleri ele alınmaktadır. Burada açıklanan teknikler, üst düzey tekniklerdir. Daha fazla bilgi için bkz. [hata ayıklayıcıyı kullanma](../debugger/debugger-basics.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Çıkış Penceresindeki Tanılama İletileri](../debugger/diagnostic-messages-in-the-output-window.md)  
 <xref:System.Diagnostics.Debug>Ve <xref:System.Diagnostics.Trace> sınıflarını, çalışma zamanı iletilerini **Çıkış** penceresine yazabileceğiniz şekilde açıklar. Bu sınıflar, belirtilen bir koşul başarısız olursa yürütmeyi kesintiye uğratmadan, yürütme ve bilgi çıkışının kesintiye girmeden bilgi çıktısını etkinleştiren çıkış yöntemlerini içerir.  
  
 [Yönetilen Koddaki Onaylar](../debugger/assertions-in-managed-code.md)  
 Yöntemler için bağımsız değişken olarak belirttiğiniz test koşullarını Yönetilen koddaki onayları açıklar `Assert` . Buna ek olarak, bu konuda örnek kod, <xref:System.Diagnostics.Debug> ve sınıf yöntemleri hakkında bilgi, <xref:System.Diagnostics.Trace> kod hata ayıklama ve yayın sürümlerindeki konular, yan etkiler, onaylama bağımsız değişkenleri, onaylama davranışını özelleştirme ve yapılandırma dosyaları sağlanmaktadır.  
  
 [Visual Basic'de Durdur Deyimleri](../debugger/stop-statements-in-visual-basic.md)  
 `Stop`Kesme noktası ayarlamaya alternatif sağlayan ifadesini açıklar. Örnek kod ayrıca, ve deyimleri arasındaki karşılaştırmaların yanı sıra, `Stop` `End` `Stop` ve `Assert` deyimleriyle birlikte da sağlanır.  
  
 [İzlenecek yol: Windows Formunda hata ayıklama](../debugger/walkthrough-debugging-a-windows-form.md)  
 Windows formu oluşturmak ve bu formun hatalarını ayıklamak için adım adım yönergeler sağlar. Yönetilen bir Windows uygulamasının standart bir bileşeni olan Windows formu, en yaygın yönetilen uygulamalardan biridir. Bu izlenecek yol, Visual C# ve Visual Basic kullanır, ancak C++ ile Windows formu oluşturma teknikleri genellikle benzerdir.  
  
 [OnStart yönteminde hata ayıklama](../debugger/how-to-debug-the-onstart-method.md)  
 Yönetilen bir Windows hizmeti yönteminde hata ayıklamanıza olanak tanımak için kod örnekleri sağlar `OnStart` . `OnStart`Bir Windows hizmeti yönteminde hata ayıklamak için, hizmetin benzetimini yapmak üzere birkaç satır kod eklemeniz gerekir.  
  
 [Karışık modda hata ayıklama](../debugger/debugging-mixed-mode-applications.md)  
 Karışık modda uygulamalarda hata ayıklamayı açıklar. Bu, yerel kodu yönetilen kodla birleştiren tüm uygulamalar anlamına gelir.  
  
 [Hata: Sistemde çekirdek hata ayıklayıcı etkinleştirildiğinden hata ayıklama mümkün değil](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)  
 Hata [!INCLUDE[win7](../includes/win7-md.md)] ayıklama modunda başlatılmış bir,,, [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)] [!INCLUDE[winxp](../includes/winxp-md.md)] [!INCLUDE[Win2kFamily](../includes/win2kfamily-md.md)] veya Windows NT sisteminde yönetilen kodda hata ayıklamaya çalıştığınızda oluşan bir hata iletisi açıklanır.  
  
 [JIT İyileştirmesi ve Hata Ayıklaması](../debugger/jit-optimization-and-debugging.md)  
 Hata ayıklama sırasında JıT iyileştirmesinin etkilerini açıklar.  
  
 [LINQ ve DLıNQ hatalarını ayıklama](../debugger/debugging-linq.md)  
 LINQ sorgularının hatalarını ayıklama tekniklerini açıklar.  
  
 [İzlenecek Yol: Paralel Uygulamada Hata Ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Paralel bir uygulamada hata ayıklamak için **paralel görevler** ve **Paralel Yığınlar** araç pencerelerinin nasıl kullanılacağını açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [IntelliTrace](../debugger/intellitrace.md)  
 Uygulamanızın yürütme geçmişini IntelliTrace ile kaydederek daha hızlı ve kolay bir şekilde hata bulun. Kaydedilen olayları ve geri doğru ilerlemeden, uygulamanın durumunu zaman içinde önemli noktalarda incelemek için çağrılar yapın. Çok sayıda kesme noktası ayarlamadan veya uygulamanızı sık yeniden başlatarak kodunuzda hata ayıklayın. Visual Studio Ultimate gerektirir.  
  
 [Uygulamaları izleme ve İşaretleme](https://msdn.microsoft.com/library/773b6fc4-9013-4322-b728-5dec7a72e743)  
 Uygulamasının, çalışırken uygulamanın yürütülmesini izlemenin ve izleme deyimlerinin kodunuzda stratejik konumlarda yerleştirilmesi için gereken bir yol olan izlemeyi açıklar. Bu konu ayrıca, izleme ve izleme, izleme anahtarları, izleme dinleyicileri, bir uygulamadaki kod izleme, uygulama koduna izleme deyimleri ekleme ve ile koşullu olarak derleme için bir giriş bağlantıları sağlar <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> .  
  
 [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)  
 <xref:System.Diagnostics.DebuggableAttribute>C++ ile yazılmış koda ekleyen bağlayıcı seçeneğini açıklar. Bu öznitelik, C++ ile iliştirme gibi hata ayıklama özelliklerini kullanmak için gereklidir.  
  
 [Windows hizmet uygulamalarında hata ayıklama](https://msdn.microsoft.com/library/63ab0800-0f05-4f1e-88e6-94c73fd920a2)  
 Windows hizmet uygulamalarında hata ayıklama, işleme ekleme, hizmetin yöntemindeki kodda hata ayıklama, ana yöntemdeki kodda hata ayıklama, `OnStart` ana yöntemdeki kod hata ayıklama, kesme noktası ayarlama ve hizmet Denetim Yöneticisi 'ni kullanarak hizmetinizi başlatma, durdurma, duraklatma ve devam etme gibi konuları sağlar.  
  
 [Hata ayıklama ve profil oluşturma](https://msdn.microsoft.com/library/4a04863e-2475-46f4-bc3f-3c11510c2a4b)  
 .NET Framework uygulamalarda hata ayıklamayı ve yapılandırma gereksinimlerini açıklar.  
  
 [Betikte ve Web uygulamalarında hata ayıklama](../debugger/debugging-web-applications-and-script.md)  
 Betiklerin ve Web uygulamalarında hata ayıklarken karşılaşabileceğiniz yaygın hata ayıklama sorunlarını ve tekniklerini açıklar.  
 Bu sürümünde eklenen yeni hata ayıklama özelliklerinin açıklaması [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 [Giriş sayfasında hata ayıklama](../debugger/debugging-in-visual-studio.md)  
 Hata ayıklama belgelerinin daha büyük bölümlerine bağlantılar sağlar. Bilgiler hata ayıklayıcı, ayarlar ve hazırlık, kesme noktaları, özel durumları işleme, düzenleme ve devam etme, yönetilen kodda hata ayıklama, hata ayıklama Visual C++ projeleri, hata ayıklama, COM ve ActiveX, hata ayıklama dll 'Leri ve Kullanıcı arabirimi başvurularında nelerin yeni olduğunu içerir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: tasarım zamanında özel Windows Forms Denetimlerinde hata ayıklama](https://msdn.microsoft.com/library/1fd83ccd-3798-42fc-85a3-6cba99467387)   
 [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)   
 [Visual Studio'da Hata Ayıklama](../debugger/debugging-in-visual-studio.md)
