---
title: 'Nasıl yapılır: Tasarımcıyı kullanarak ClickOnce uygulamalarında URL etkinleştirmeyi devre dışı bırakma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 27690ab275d0c7ef2a090fa8ef2e42887ae9daeb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153808"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Nasıl yapılır: Tasarımcıyı Kullanarak ClickOnce Uygulamalarında URL Etkinleştirmeyi Devre Dışı Bırakma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Genellikle bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama, bir Web sunucusundan yüklendikten hemen sonra otomatik olarak başlatılır. Güvenlik nedenleriyle, bu davranışı devre dışı bırakmayı ve kullanıcılara bunun yerine **Başlangıç** menüsünden uygulamayı başlatmasını söylemeniz gerekebilir. Aşağıdaki yordamda URL etkinleştirmeyi devre dışı bırakma açıklanmaktadır.  
  
 Bu teknik, yalnızca [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] kullanıcının bilgisayarında bir Web sunucusundan yüklenen uygulamalar için kullanılabilir. Yalnızca kendi URL 'SI kullanılarak başlatılabilen, yalnızca çevrimiçi uygulamalar için kullanılamaz. Yalnızca çevrimiçi ve yüklü uygulamalar arasındaki fark hakkında daha fazla bilgi için bkz. [ClickOnce dağıtım stratejisi seçme](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Bu yordam kullanır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Ayrıca, kullanarak bu görevi gerçekleştirebilirsiniz [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] . Daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce UYGULAMALARıNıN URL etkinleştirmeyi devre dışı bırakma](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Uygulamanız için URL etkinleştirmeyi devre dışı bırakmak için  
  
1. **Çözüm Gezgini**' de proje adına sağ tıklayın ve **Özellikler**' e tıklayın.  
  
2. **Özellikler** sayfasında, **Yayımla** sekmesine tıklayın.  
  
3. **Seçenekler**’e tıklayın.  
  
4. **Bildirimler**' e tıklayın.  
  
5. **Uygulamanın BIR URL aracılığıyla etkinleştirilmesini engelle**etiketli onay kutusunu seçin.  
  
6. Uygulamanızı dağıtın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce Uygulamalarını Yayımlama](../deployment/publishing-clickonce-applications.md)
