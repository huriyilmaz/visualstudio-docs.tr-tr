---
title: Sorun giderme ve bilinen sorunlar (Unity için Visual Studio Araçları) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: troubleshooting
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
caps.latest.revision: 7
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: ad085cc6c41714a551fbb344274e6d0f164ab67e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297662"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Sorun Giderme ve Bilinen Sorunlar (Unity için Visual Studio Araçları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde, bilinen sorunların açıklamalarını Unity için Visual Studio Araçları ile sık karşılaşılan sorunlara çözümler bulmak ve Unity için Visual Studio Araçları hata bildirimi tarafından geliştirilmesine nasıl yardımcı olabileceğini öğrenin.  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Unity için Visual Studio Araçları bazı yaygın sorunları çözümlemek için aşağıdaki bölümlere bakın.  
  
### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>UnityVS Unity için Visual Studio Araçları 'e geçiş  
 UnityVS 'yi Unity için Visual Studio Araçları 'e geçiriyorsanız Unity projeleriniz için yeni Visual Studio çözümleri oluşturmanız gerekir.  
  
##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>Unity projenizi UnityVS 1,8 ' den Unity için Visual Studio Araçları 1,9 ' ye geçirmek için  
  
1. Unity projenizden eski çözüm ve proje dosyalarını silin. Unity projenizin kök dizininde, Visual Studio. sln ve. * proj dosyalarını bulun ve tümünü silin.  
  
2. Unity için Visual Studio Araçları paketini Unity projenize aktarın. VSTU paketini içeri aktarma hakkında daha fazla bilgi için [Başlarken](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) sayfasında Unity için Visual Studio Araçları yapılandırma konusuna bakın.  
  
3. Yeni çözüm ve proje dosyaları oluşturun. Bunları şimdi oluşturmak istiyorsanız, Unity düzenleyicisinde, ana menüdeki **Visual Studio Araçları**, **proje dosyaları oluştur**' u seçin. Aksi takdirde, isterseniz bu adımı atlayabilirsiniz; Unity için Visual Studio Araçları, **Visual Studio Araçları**seçtiğinizde **Visual Studio 'da açık olan**yeni dosyaları otomatik olarak oluşturacaktır.  
  
### <a name="visual-studio-wont-load-the-solution-that-visual-studio-tools-for-unity-created"></a>Visual Studio Unity için Visual Studio Araçları oluşturulan çözümü yüklemez  
 Daha fazla bilgi için [Bu StackOverflow sorusunun yanıtını](https://stackoverflow.com/questions/20086755/unityvs-visual-studio-can-not-open/24035907#24035907)inceleyin.  
  
### <a name="on-windows-8-visual-studio-asks-to-download-the-unity-target-framework"></a>Windows 8 ' de, Visual Studio 'Nun Unity hedef çerçevesini indirmesini ister  
 UnityVS, Windows 8 ' de varsayılan olarak yüklü olmayan .NET Framework 3,5 gerektirir. Bu sorunu gidermek için, .NET Framework 3,5 'yi indirme ve yükleme yönergelerini izleyin.  
  
## <a name="known-issues"></a>Bilinen Sorunlar  
 Bilinen sorunlar vardır, hata ayıklayıcı Unity'nın daha eski C# Derleyici sürümü ile nasıl etkileştiğini gelen neden Visual Studio Araçları Unity için. Bu sorunları gidermeye yardımcı olmak için çalışıyoruz, ancak bu sırada aşağıdaki sorunlarla karşılaşabilirsiniz.  
  
- Hata ayıklama sırasında Unity bazen kilitleniyor.  
  
- Unity bazen hata ayıklama sırasında donuyor.  
  
- İçine ve dışına yöntemleri bazen Adımlama özellikle yineleyiciler veya switch deyimleri içinde yanlış bir şekilde davranır.  
  
## <a name="reporting-errors"></a>Raporlama hataları  
 Lütfen kilitlenen, donuyor veya diğer hatalarla karşılaşırsanız, hata raporları göndermek kalite Unity için Visual Studio Araçları'nın geliştirmemize yardımcı olun. Bu, bize araştırmak ve Unity için Visual Studio Araçları'ndaki sorunları gidermeye yardımcı olur. Teşekkür ederiz!  
  
### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Visual Studio donuyor olduğunda bir hata bildirme  
 Visual Studio bazen Unity için Visual Studio Araçları ile hata ayıklama sırasında donuyor raporlar vardır, ancak bu sorunu anlamak için daha fazla veriye ihtiyacımız. Bize aşağıdaki adımları izleyerek araştırmanıza yardımcı olabilir.  
  
##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Visual Studio Unity için Visual Studio Araçları ile hata ayıklama sırasında donuyor bildirmek için  
  
1. Visual Studio'nun yeni bir örneğini açın.  
  
2. İşleme İliştir'iletişim kutusunda açın. Yeni Visual Studio örneğinde ana menüsündeki seçin **hata ayıklama**, **iliştirme**.  
  
3. Hata ayıklayıcı, Visual Studio dondurulmuş örneğine ekleyin. İçinde **iliştirme** iletişim kutusunda, Visual Studio'dan dondurulmuş örneğini seçin **kullanılabilir işlemler** tablosuna ve sonra seçin **iliştirme** düğmesi.  
  
4. Hata ayıklayıcı duraklatın. Visual Studio 'nun yeni örneğinde, ana menüdeki **Hata Ayıkla**, **Tümünü kes** ' i seçin veya **Ctrl + Alt + Break**tuşlarına basın.  
  
5. Bir iş parçacığı dökümü oluşturun. Komut penceresi, aşağıdaki komutu girin ve **ENTER**tuşuna basın.  
  
   ```powershell  
   Debug.ListCallStack /AllThreads /ShowExternalCode  
   ```  
  
    Yapmanız gerekebilecek **komut** pencere ilk görünür. Visual Studio'da ana menüde seçin **görünümü**, **diğer Windows**, **komut penceresi**.  
  
6. Son olarak, iş parçacığı-dökümü gönderme [ vstusp@microsoft.com ](mailto:vstusp@microsoft.com), ne zaman yapmakta olduğunuz açıklaması ile birlikte Visual Studio dondurulmuş hale geldi.
