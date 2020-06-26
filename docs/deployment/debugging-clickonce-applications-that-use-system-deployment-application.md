---
title: System. Deployment. Application kullanan ClickOnce uygulamalarında hata ayıklama
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 203f1edc2e29bbbc34fb39e6aa01c1b56bf20e91
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382659"
---
# <a name="debug-clickonce-applications-that-use-systemdeploymentapplication"></a>System. Deployment. Application kullanan ClickOnce uygulamalarında hata ayıklama
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]' De, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım, bir uygulamanın nasıl güncelleştirileceğini yapılandırmanıza olanak tanır. Bununla birlikte, gelişmiş dağıtım özelliklerini kullanmanız ve özelleştirmeniz gerekiyorsa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , tarafından sağlanmış olan dağıtım nesne modeline erişmeniz gerekir <xref:System.Deployment.Application> . API 'leri, gibi <xref:System.Deployment.Application> Gelişmiş görevler için kullanabilirsiniz:

- Uygulamanızda "Şimdi Güncelleştir" seçeneği oluşturuluyor

- Çeşitli uygulama bileşenlerinin koşullu, isteğe bağlı İndirmeleri

- Doğrudan uygulamayla tümleştirilmiş güncelleştirmeler

- İstemci uygulamasının her zaman güncel olduğunu garanti etme

  <xref:System.Deployment.Application>API 'ler yalnızca bir uygulama teknoloji ile dağıtıldığında çalıştığı için [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , bunları hata ayıklamanın tek yolu kullanarak uygulamayı dağıtıp [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] hata ayıklamaktır. Hata ayıklayıcıyı yeterince erken iliştirmek zor olabilir çünkü bu kod, hata ayıklayıcıyı iliştirebilmeniz için genellikle uygulama başlatıldığında ve yürütüldüğünde çalışır. Güncelleştirme, kodunuzun veya isteğe bağlı koddan önce molalar (veya Visual Basic projeler için duraklar) yerleştirbir çözümdür.

  Önerilen hata ayıklama tekniği aşağıdaki gibidir:

1. Başlamadan önce, simgenin (. pdb) ve kaynak dosyalarının arşivlendiğinizden emin olun.

2. Uygulamanın sürüm 1 ' i dağıtın.

3. Yeni bir boş çözüm oluşturun. **Dosya** menüsünde **Yeni**' ye ve ardından **Proje**' ye tıklayın. **Yeni proje** iletişim kutusunda, **diğer proje türleri** düğümünü açın ve ardından **Visual Studio çözümleri** klasörünü seçin. **Şablonlar** bölmesinde **boş çözüm**' ü seçin.

4. Arşivlenmiş kaynak konumunu bu yeni çözümün özelliklerine ekleyin. **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın ve ardından **Özellikler**' e tıklayın. **Özellik sayfaları** iletişim kutusunda, **Hata Ayıkla kaynak dosyaları**' nı seçin ve ardından arşivlenen kaynak kodun dizinini ekleyin. Aksi takdirde, kaynak dosya yolları. pdb dosyasına kaydedildiğinden hata ayıklayıcı güncel olmayan kaynak dosyalarını bulur. Hata ayıklayıcı güncel olmayan kaynak dosyaları kullanıyorsa, kaynağın eşleşmez olduğunu söyleyen bir ileti görürsünüz.

5. Hata ayıklayıcının *. pdb* dosyalarını bulabileceği şekilde emin olun. Bunları uygulamanızla dağıttıysanız, hata ayıklayıcı onları otomatik olarak bulur. Her zaman önce söz konusu derlemenin yanına bakar. Aksi takdirde, arşiv yolunu **sembol dosyası (. pdb) konumlarına** eklemeniz gerekir (Bu seçeneğe erişmek Için, **Araçlar** menüsünden **Seçenekler**' e tıklayın, ardından **hata ayıklama** düğümünü açın ve **semboller**' e tıklayın).

6. `CheckForUpdate`Ve `Download` / `Update` Yöntem çağrıları arasında neler olduğunu hata ayıklayın.

    Örneğin, güncelleştirme kodu şu şekilde olabilir:

   ```vb
       Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
           If My.Application.Deployment.IsNetworkDeployed Then

               If (My.Application.Deployment.CheckForUpdate()) Then

                   My.Application.Deployment.Update()
                   Application.Restart()

               End If

           End If
       End Sub
   ```

7. Sürüm 2 ' ye dağıtın.

8. Sürüm 2 için bir güncelleştirmeyi indirdiği için hata ayıklayıcıyı sürüm 1 uygulamasına iliştirmeye çalışın. Alternatif olarak, `System.Diagnostics.Debugger.Break` yöntemini veya yalnızca Visual Basic kullanabilirsiniz `Stop` . Kuşkusuz, bu yöntem çağrılarını üretim kodunda bırakmamanız gerekir.

    Örneğin, bir Windows Forms uygulaması geliştirdiğinizi ve bu yöntemde güncelleştirme mantığını içeren bir olay işleyiciniz olduğunu varsayalım. Bu, hata ayıklamak için, düğmeye basılmadan önce ekleyin, sonra bir kesme noktası ayarlayın (uygun arşivlenmiş dosyayı açıp kesme noktasını orada ayarladığınızdan emin olun).

   <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> <xref:System.Deployment.Application> Yalnızca uygulama dağıtıldığında API 'leri çağırmak için özelliğini kullanın; API 'ler, içinde hata ayıklama sırasında çağrılmamalıdır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Deployment.Application>