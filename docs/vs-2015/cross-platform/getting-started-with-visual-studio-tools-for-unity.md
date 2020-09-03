---
title: Unity için Visual Studio Araçları kullanmaya başlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
caps.latest.revision: 12
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: f110b8d6f7ab05d5a1b6942cd9ec599a8d8619b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299831"
---
# <a name="getting-started-with-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları ile Başlarken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde, Visual Studio ile çalışmak için Unity için Visual Studio Araçları yüklemeyi ve Unity projenizi yapılandırmayı öğreneceksiniz.  
  
> [!IMPORTANT]
> Unity 5,2, proje kurulumunu kolaylaştıran Unity için Visual Studio Araçları 2,1 için yerleşik destek ekler. Bundan faydalanmak için, Windows 'da Unity sürüm 5.2.0 veya üzeri ve sürüm 2,1 veya üstünü Unity için Visual Studio Araçları gerekir.  
  
## <a name="prerequisites"></a>Ön koşullar  
 Unity için Visual Studio Araçları kullanmak için şunlar gerekir:  
  
- **Visual Studio 'Nun Visual** Studio Community, Professional, Premium veya Enterprise gibi uzantıları destekleyen bir sürümü. Visual Studio Community 'yi ücretsiz olarak indirebilirsiniz.  
  
     [Visual Studio Community 'yi indirin](https://www.visualstudio.com/downloads/download-visual-studio-vs)  
  
- **Unity** sürüm 4.0.0 veya üzeri; Unity için Visual Studio Araçları sürüm 2,1 veya üzeri için yerleşik desteğin avantajlarından faydalanmak için **Unity** sürüm 5.2.0 veya üzeri.  
  
     [Unity 'yi indirin](https://unity3d.com/get-unity/download)  
  
## <a name="install-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları yüklensin  
 Visual Studio galerisinden Unity için Visual Studio Araçları indirip yükleyin. Visual Studio sürümünüz için doğru paketi yüklemeniz gerekir. Unity 5,2 veya üzeri sürümlerde VSTU için yerleşik destekten faydalanmak için Unity için Visual Studio Araçları sürüm 2,1 veya üstünü yüklediğinizden emin olun.  
  
- Visual Studio 2015 Community, Visual Studio 2015 Professional veya Visual Studio 2015 Enterprise için:  
  
     [Unity için Visual Studio 2015 araçlarını indirin](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)  
  
- Visual Studio 2013 Community, Visual Studio 2013 Professional veya Visual Studio 2013 Premium için:  
  
     [Unity için Visual Studio 2013 araçları 'nı indirin](https://visualstudiogallery.msdn.microsoft.com/20b80b8c-659b-45ef-96c1-437828fe7cf2)  
  
- Visual Studio 2012 Professional veya Visual Studio 2012 Premium için:  
  
     [Unity için Visual Studio 2012 araçlarını indirin](https://visualstudiogallery.msdn.microsoft.com/7ab11d2a-f413-4ed6-b3de-ff1d05157714)  
  
- Visual Studio 2010 Professional veya Visual Studio 2010 Premium için:  
  
     [Unity için Visual Studio 2010 araçlarını indirin](https://visualstudiogallery.msdn.microsoft.com/6e536faa-ce73-494a-a746-6a14753015f1)  
  
> [!NOTE]
> Visual Studio 'nun Express sürümleri, Unity için Visual Studio Araçları gibi uzantıları desteklemez. Visual Studio Community, Visual Studio 'nun Unity için Visual Studio Araçları ve diğer uzantıları destekleyen ücretsiz bir sürümüdür. Çoğu kullanıcı için, Visual Studio Community Express 'ten daha iyi bir seçimdir.  
  
## <a name="your-first-unity-project-with-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları olan ilk Unity projeniz  
 Artık ihtiyacınız olan her şeye sahip olduğunuza göre, Visual Studio ile ilk Unity projeniz için hazır olursunuz. Unity projenizin kurulması, hangi Unity ve Unity için Visual Studio Araçları sürümlerinin yüklü olduğuna bağlı olarak farklılık gösteren bir ayardır. Unity için Visual Studio Araçları Unity sürümü ve yüklemiş olduğunuz için aşağıdaki adımları izleyin.  
  
### <a name="unity-52-and-higher-requires-vstu-21-or-higher"></a>Unity 5,2 ve üzeri (VSTU 2,1 veya üzeri gerekir)  
 Unity 5,2 ' den başlayarak, artık Visual Studio Araçları unitypackage 'ı projelerinize aktarmanız gerekmez. Projeniz bu unitypackage 'a aktarıldığında Unity 5,2 bunu yoksayar ve yüklü konumundan Unity için Visual Studio Araçları doğrudan yükler.  
  
#### <a name="1---create-a-unity-project"></a>1-Unity projesi oluşturma  
 Zaten Unity ile karşılaşırsanız, yeni bir proje oluşturabilir veya kendi kendinize bir tane yükleyebilirsiniz. Unity 'nin önceki bir sürümüyle Unity için Visual Studio Araçları kullanmak üzere Visual Studio Araçları unitypackage 'ı içeri aktarmış bir proje yüklüyorsanız, UnityVS dizinini silerek kaldırmanız önerilir.  
  
 Aksi takdirde, Unity için yeni başladıysanız, temel bir öğreticiyle küçük bir başlangıç yapın. ' Den başlayabileceğinizi örnek projelerde ve Unity ile kendi oyununuzu oluşturmak için öğrenirsiniz. Unity öğrenme sayfasında birkaç farklı oyun için kullanımı kolay öğreticiler vardır.  
  
 [Öğreticiler – Unity öğreni sayfası](https://learn.unity.com/tutorials)  
  
#### <a name="2---configure-unity-editor-to-use-visual-studio-tools-for-unity"></a>2-Unity için Visual Studio Araçları kullanmak için Unity düzenleyicisini yapılandırma  
 Projenizin Unity için Visual Studio Araçları kullanmasını sağlamak için, Visual Studio 'Yu dış betik düzenleyicisi olarak ayarlamanız yeterlidir. Unity düzenleyicisinde, ana menüden **Düzenle, Tercihler**' i seçin. ardından, **Unity tercihleri** Iletişim kutusunda **dış araçlar**' ı seçin. Ardından, **dış betik Düzenleyicisi** özelliğini kullanmak Istediğiniz Visual Studio sürümüne ayarlayın (Unity için Visual Studio Araçları Visual Studio 'nun bu sürümü için yüklü olmalıdır) ve **Düzenleyici iliştirme** özelliğinin ayarlandığından emin olun.  
  
 Unity için Visual Studio Araçları için yerleşik desteğin artık etkinleştirildiğinden emin olmak için **Unity hakkında** iletişim kutusuna bakın. Unity düzenleyicisinde, ana menüdeki **Yardım ' ı, Unity hakkında** ' yı seçin. Unity için Visual Studio Araçları yüklenip doğru yapılandırılmışsa, **Unity hakkında** iletişim kutusunun sol alt köşesinde bir ileti görürsünüz.  
  
 Son olarak, **yapı ayarları** sayfasından bir yapı hedefi ayarladığınızdan ve **betik hata ayıklamanın** etkinleştirildiğinden emin olun.  
  
 ![Hata ayıklama için Unity derleme ayarlarını yapılandırın.](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
#### <a name="3---launch-visual-studio-from-the-unity-editor"></a>3-Unity düzenleyicisinden Visual Studio 'Yu başlatma  
 Unity 5,2 ' den başlayarak **Visual Studio Araçları** uzantısı menüsüne Visual Studio 'yu başlatmak veya Unity için Visual Studio Araçları yapılandırmak için artık gerek yoktur. Bunun yerine, Visual Studio dış betik düzenleyiciniz olarak yapılandırıldıktan sonra Unity düzenleyicisinden betik dosyasını seçmeniz yeterlidir ve kodunuz Visual Studio 'da açılır.  
  
### <a name="previous-versions-of-unity-pre-52"></a>Unity 'nin önceki sürümleri (5,2 öncesi)  
 Unity 5,2 ' den önce Unity için Visual Studio Araçları için yerleşik destek yoktu. Bunun yerine, her proje Unity için Visual Studio Araçları kullanmak için Visual Studio Araçları unitypackage 'ı içeri aktarıp diğer proje ayarlarını yapılandırmalıdır.  
  
#### <a name="1---create-a-unity-project"></a>1-Unity projesi oluşturma  
 Zaten Unity ile karşılaşırsanız, yeni bir proje oluşturabilir veya kendi kendinize bir tane yükleyebilirsiniz. Yeni bir proje başlatıyorsanız, onu oluştururken Visual Studio Araçları unitypackage öğesini içeri aktarın.  
  
 Aksi takdirde, Unity için yeni başladıysanız, temel bir öğreticiyle küçük bir başlangıç yapın. ' Den başlayabileceğinizi örnek projelerde ve Unity ile kendi oyununuzu oluşturmak için öğrenirsiniz. Unity öğrenme sayfasında birkaç farklı oyun için kullanımı kolay öğreticiler vardır.  
  
 [Öğreticiler – Unity öğreni sayfası](https://learn.unity.com/tutorials)  
  
#### <a name="2---configure-unity-editor-to-use-visual-studio-tools-for-unity"></a>2-Unity için Visual Studio Araçları kullanmak için Unity düzenleyicisini yapılandırma  
 Mevcut bir Unity projesinden başlıyorsanız veya projeyi oluştururken Visual Studio Araçları unitypackage 'ı içeri aktarmadıysanız, unitypackage 'ı şimdi içeri aktarmanız gerekir. Unity düzenleyicisinde, ana menüdeki **varlıklar, Içeri aktarma paketi, Visual Studio 2015 Araçları '** nı seçin (yüklediğiniz Visual Studio sürümü için bir seçenek görmeniz gerekir).  
  
 ![VSTU paketini Unity projenize aktarın.](../cross-platform/media/vstu-configure-unity-import-vstu.png "vstu_configure_unity_import_vstu")  
  
 Son olarak, **yapı ayarları** sayfasından bir yapı hedefi ayarladığınızdan ve **betik hata ayıklamanın** etkinleştirildiğinden emin olun.  
  
 ![Hata ayıklama için Unity derleme ayarlarını yapılandırın.](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
#### <a name="3---launch-visual-studio-from-unity-editor"></a>3-Unity düzenleyicisinden Visual Studio 'Yu başlatma  
 Son adım, Unity 'den Visual Studio 'Yu başlatmadır. Böylece projeniz için bir Visual Studio çözümü oluşturulur ve ardından Visual Studio 'da açılır.  
  
 Unity düzenleyicisinde, ana menüdeki **Visual Studio Araçları, Visual Studio 'Da aç '** ı seçin.  
  
 ![Visual Studio 'da Unity projenizi açın.](../cross-platform/media/vstu-configure-open-in-visual-studio.png "vstu_configure_open_in_visual_studio")  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Visual Studio 'da Unity projenizde çalışma ve hata ayıklama hakkında bilgi edinmek için bkz. [Using Unity için Visual Studio Araçları](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Unity giriş sayfası](https://unity.com/)
