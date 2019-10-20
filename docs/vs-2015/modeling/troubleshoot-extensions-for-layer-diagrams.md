---
title: Katman diyagramları için uzantı sorunlarını giderme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: troubleshooting
helpviewer_keywords:
- layer diagrams, extension errors
- layer diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dd4560673259373b68b370e73a43de424fb7bdb7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658471"
---
# <a name="troubleshoot-extensions-for-layer-diagrams"></a>Katman diyagramları için genişletme sorunlarını giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, katman modeli uzantıları oluştururken karşılaşabileceğiniz bazı sorunları ele almaktadır.

#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-layer-diagrams-in-the-experimental-instance-of-includevsprvsincludesvsprvs-mdmd"></a>Uzantımda hata ayıklamak için F5 'e bastığımda, komutlarım, hareket işleyicileri, doğrulama uzantıları veya özel özellikler [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Deneysel örneğindeki katman diyagramlarında görünmez

1. Uzantı çözümünüzü [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] deneysel örneğinde açın ve **Derle** menüsünde **çözümü yeniden derle**' ye tıklayın.

2. @No__t_2 Deneysel örneğini başlatmak için **F5** veya **CTRL + F5** tuşlarına basın. Bir katman diyagramı açın ve uzantınızı test edin.

   Gerekirse sonraki yordamla devam edin.

#### <a name="an-old-version-of-my-extension-runs"></a>Uzantımın eski bir sürümü çalışıyor.

1. @No__t_0 deneysel bir örneğinin çalıştığından emin olun.

2. Şu klasörü silin:%LocalAppData%\Microsoft\VisualStudio \\ [sürüm] \ComponentModelCache

   > [!NOTE]
   > % LocalAppData% genellikle *DriveName*: \Users \\*UserName*\AppData\Local.

   Gerekirse sonraki yordamla devam edin.

#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Doğrulama sonuçlarım 'ın eski bir sürümü görüntüleniyor veya doğrulama yöntemi çağrılmadı.

1. @No__t_0 deneysel örneğinde, **Yapı** menüsünde **Çözümü Temizle**' ye tıklayın. Bu, önceki doğrulama analizine ait önbelleğe alınmış sonuçları temizler.

2. Modelinizdeki katmanların kod öğeleriyle ilişkili olduğundan ve modelde en az bir bağımlılık bağlantısı olduğundan emin olun. Doğrulanacak bir şey yoksa doğrulama çağrılmaz.

3. Düzenli kesme noktaları, ayrı bir işlemde çalıştığından doğrulama yönteminde çalışmayabilir. Yönteminizin içinde ilerlemek istiyorsanız `System.Diagnostics.Debugger.Launch()` bir çağrı eklemeniz gerekir.

4. Katman doğrulama projenizdeki **Source. Extension. valtmanifest** dosyasında, **Içerik**altında hem **MEF bileşen** öğesi hem de **özel uzantı türü** öğesi eklediğinizden emin olun.

## <a name="see-also"></a>Ayrıca Bkz.
 [Katman diyagramlarını genişletme](../modeling/extend-layer-diagrams.md)
