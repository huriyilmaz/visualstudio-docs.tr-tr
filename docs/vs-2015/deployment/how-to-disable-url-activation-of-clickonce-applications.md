---
title: 'Nasıl yapılır: ClickOnce uygulamalarında URL etkinleştirmeyi devre dışı bırakma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 75a98706858323693ec01ec3c3420a6d2d25ffef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697220"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Nasıl yapılır: ClickOnce Uygulamalarında URL Etkinleştirmeyi Devre Dışı Bırakma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Genellikle, bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama bir Web sunucusundan yüklendikten hemen sonra otomatik olarak başlatılır. Güvenlik nedenleriyle, bu davranışı devre dışı bırakmayı ve kullanıcılara bunun yerine başlangıç menüsünden uygulamayı **başlatmasını** söylemeniz gerekebilir. Aşağıdaki yordamda URL etkinleştirmeyi devre dışı bırakma açıklanmaktadır.  
  
 Bu teknik, yalnızca [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] kullanıcının bilgisayarında bir Web sunucusundan yüklenen uygulamalar için kullanılabilir. Yalnızca kendi URL 'SI kullanılarak başlatılabilen, yalnızca çevrimiçi uygulamalar için kullanılamaz. Yalnızca çevrimiçi ve yüklü uygulamalar arasındaki fark hakkında daha fazla bilgi için bkz. [ClickOnce dağıtım stratejisi seçme](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Bu yordam [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] MageUI.exe aracını kullanır. Bu araç hakkında daha fazla bilgi için bkz. [MageUI.exe (bildirim oluşturma ve düzenleme aracı, grafik istemci)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). Ayrıca, bu yordamı kullanarak da gerçekleştirebilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Uygulamanız için URL etkinleştirmeyi devre dışı bırakmak için  
  
1. Dağıtım bildiriminizi MageUI.exe ' de açın. Henüz bir tane oluşturmadıysanız [Izlenecek yol: ClickOnce uygulamasını El Ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)' daki adımları izleyin.  
  
2. **Dağıtım seçenekleri** sekmesini seçin.  
  
3. **Yüklendikten sonra otomatik olarak uygulamayı çalıştır** onay kutusunu temizleyin.  
  
4. Bildirimi kaydedin ve imzalayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce Uygulamalarını Yayımlama](../deployment/publishing-clickonce-applications.md)
