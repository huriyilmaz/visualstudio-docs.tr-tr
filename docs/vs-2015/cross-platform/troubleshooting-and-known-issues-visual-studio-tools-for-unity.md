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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297662"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Sorun Giderme ve Bilinen Sorunlar (Unity için Visual Studio Araçları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde, Unity için Visual Studio Araçları, bilinen sorunların açıklamalarıyla ilgili sık karşılaşılan sorunlara çözümler bulacaksınız ve hataları bildirerek Unity için Visual Studio Araçları nasıl iyileştirebileceğinizi öğreneceksiniz.  
  
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
 Unity için Visual Studio Araçları hata ayıklayıcının, C# derleyicisinin daha eski sürümü ile nasıl etkileşime gireceğini belirten bilinen sorunlar vardır. Bu sorunları gidermeye yardımcı olmak için çalışıyoruz, ancak bu sırada aşağıdaki sorunlarla karşılaşabilirsiniz.  
  
- Hata ayıklarken Unity bazen kilitleniyor.  
  
- Hata ayıklama sırasında Unity bazen donuyor.  
  
- Yöntemlerin içine ve dışına adımla bazen, özellikle yineleyiciler içinde veya switch deyimlerinde yanlış bir şekilde davranır.  
  
## <a name="reporting-errors"></a>Raporlama hataları  
 Kilitlenme, dondurur veya diğer hatalarla karşılaşdığınızda hata raporları göndererek Unity için Visual Studio Araçları kalitesini iyileştirmemize yardımcı olun. Bu, Unity için Visual Studio Araçları sorunları araştırmamıza ve gidermenize yardımcı olur. Teşekkür ederiz!  
  
### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Visual Studio donuyor olduğunda hata bildirme  
 Unity için Visual Studio Araçları ile hata ayıklarken Visual Studio 'Nun bazen donmasına neden olan raporlar var, ancak bu sorunu anlamak için daha fazla veri gerekir. Aşağıdaki adımları izleyerek araştırmamıza yardımcı olabilirsiniz.  
  
##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları hata ayıklarken Visual Studio 'Nun donuyor olduğunu bildirmek için  
  
1. Visual Studio 'nun yeni bir örneğini açın.  
  
2. Işleme Iliştir iletişim kutusunu açın. Visual Studio 'nun yeni örneğinde, ana menüdeki **Hata Ayıkla**, **İşleme İliştir**' i seçin.  
  
3. Hata ayıklayıcıyı Visual Studio 'nun dondurulmuş örneğine iliştirin. **Işleme İliştir** iletişim kutusunda, **kullanılabilir Işlemler** tablosundan Visual Studio 'nun dondurulmuş örneğini seçin ve **Ekle** düğmesini seçin.  
  
4. Hata ayıklayıcıyı duraklatın. Visual Studio 'nun yeni örneğinde, ana menüdeki **Hata Ayıkla**, **Tümünü kes** ' i seçin veya **Ctrl + Alt + Break**tuşlarına basın.  
  
5. İş parçacığı oluşturma-döküm. Komut penceresi, aşağıdaki komutu girin ve **ENTER**tuşuna basın.  
  
   ```powershell  
   Debug.ListCallStack /AllThreads /ShowExternalCode  
   ```  
  
    Önce **komut** penceresini görünür yapmanız gerekebilir. Visual Studio 'da, ana menüden **Görünüm**, **diğer pencereler**, **komut penceresi**' ni seçin.  
  
6. Son olarak, iş parçacığı dökümünü [vstusp@microsoft.com](mailto:vstusp@microsoft.com) , Visual Studio dondurulmuş hale geldiğinde ne yaptığınızın bir açıklamasıyla birlikte gönderin.
