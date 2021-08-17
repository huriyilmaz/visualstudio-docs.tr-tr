---
title: System.Deployment.Application ClickOnce uygulamalarda hata ayıklama
description: System.Deployment.Application tarafından ClickOnce nesne modeline erişerek gelişmiş dağıtım özelliklerini kullanmayı ve özelleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: d91b59b6f4eb86c905fcddd28dc5298b1a18f761
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080669"
---
# <a name="debug-clickonce-applications-that-use-systemdeploymentapplication"></a>System.Deployment.Application ClickOnce uygulama hata ayıklama
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 'de, dağıtım bir uygulamanın nasıl güncelleştirilmiş olduğunu yapılandırmanızı sağlar. Ancak, gelişmiş dağıtım özelliklerini kullanmak ve özelleştirmek için, tarafından sağlanan dağıtım [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nesne modeline erişmeniz <xref:System.Deployment.Application> gerekir. API'leri <xref:System.Deployment.Application> aşağıdakiler gibi gelişmiş görevler için kullanabilirsiniz:

- Uygulamanıza "Şimdi Güncelleştir" seçeneği oluşturma

- Çeşitli uygulama bileşenlerinin koşullu, isteğe bağlı indirmeleri

- Doğrudan uygulamayla tümleştirilmiş güncelleştirmeler

- İstemci uygulamasının her zaman güncel olduğunu garanti

  API'ler yalnızca bir uygulama teknolojiyle dağıtıldığında çalışır, bu uygulamanın hata ayıklaması için tek yol kullanarak uygulamayı dağıtmak, buna eklemek ve ardından <xref:System.Deployment.Application> [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] hata [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ayıklamaktır. Hata ayıklayıcıyı eklemeden önce bu kod genellikle uygulama başlatıldığında ve yürütülürken çalıştırılana kadar hata ayıklayıcısını yeterince erken eklemek zor olabilir. Çözüm, güncelleştirme denetim kodunuz veya isteğe bağlı kodunuz Visual Basic kesmeler (veya projeler için duraklar) yapmaktır.

  Önerilen hata ayıklama tekniği aşağıdaki gibidir:

1. Başlamadan önce sembol (.pdb) ve kaynak dosyaların arşivlenmiş olduğundan emin olun.

2. Uygulamanın 1. sürümünü dağıtın.

3. Yeni bir boş çözüm oluşturun. Dosya menüsünde **Yeni'ye** **tıklayın** ve ardından öğesini **Project.** Yeni **Project** iletişim kutusunda Diğer Project **Türleri** düğümünü açın ve Visual Studio **Klasörünü** seçin. Şablonlar **bölmesinde Boş** Çözüm'e **tıklayın.**

4. Arşivlenmiş kaynak konumunu bu yeni çözümün özelliklerine ekleyin. Bu **Çözüm Gezgini,** çözüm düğümüne sağ tıklayın ve ardından Özellikler'e **tıklayın.** Özellik **Sayfaları iletişim kutusunda** Kaynak Dosyalarda **Hata Ayıkla'ya** tıklayın ve ardından arşivlenmiş kaynak kodunun dizinini ekleyin. Aksi takdirde, kaynak dosya yolları .pdb dosyasına kaydedildikleri için hata ayıklayıcı güncel olmayan kaynak dosyaları bulur. Hata ayıklayıcısı güncel olmayan kaynak dosyaları kullanıyorsa, kaynağın eşleşme olmadığını söyleyen bir iletiyle karşılaşabilirsiniz.

5. Hata ayıklayıcının *.pdb dosyalarını bula olduğundan emin* olun. Bunları uygulamanıza dağıttıysanız, hata ayıklayıcı bunları otomatik olarak bulur. Her zaman önce söz konusu derlemenin yanında görünüyor. Aksi takdirde, arşiv yolunu Sembol dosyası **(.pdb)** konumlarına eklemeniz gerekir (bu  seçen bilgilere erişmek için  Araçlar menüsünden Seçenekler'e **tıklayın,** ardından Hata Ayıklama düğümünü açın ve Semboller'e **tıklayın).**

6. ve yöntem çağrıları arasında ne olduğunu `CheckForUpdate` `Download` / `Update` ayıklar.

    Örneğin, güncelleştirme kodu aşağıdaki gibi olabilir:

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

7. Sürüm 2'yi dağıtın.

8. Sürüm 2 için bir güncelleştirme indirdiği için hata ayıklayıcıyı sürüm 1 uygulamasına eklemeye çalışma. Alternatif olarak yöntemini kullanabilir veya `System.Diagnostics.Debugger.Break` yalnızca `Stop` Visual Basic. Elbette, bu yöntem çağrılarını üretim kodunda bırakmama gerekir.

    Örneğin, bir Windows Forms uygulaması geliştirdiğiniz ve içinde güncelleştirme mantığı olan bu yöntem için bir olay işleyiciniz olduğunu varsayalım. Hata ayıklamak için düğmeye basmadan önce ekleme yapmanız ve ardından bir kesme noktası ayarlamanız gerekir (uygun arşivlenmiş dosyayı açıp kesme noktası ayartığınızdan emin olun).

   API'leri yalnızca uygulama dağıtıldığında çağırmak için özelliğini kullanın; API'ler içinde hata <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> <xref:System.Deployment.Application> ayıklama sırasında çağrılmamalı. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Deployment.Application>