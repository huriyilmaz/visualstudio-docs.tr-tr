---
title: Tasarımcı kullanarak ClickOnce uygulamalarında URL etkinleştirmeyi devre dışı bırakma
description: Visual Studio kullanarak ClickOnce uygulaması için otomatik başlatmayı devre dışı bırakmayı, kullanıcıların uygulamayı Başlat menüsünden başlatması gerekir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c243b0e0565c082e05fd15a1e02aa0507120e16b
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350016"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Nasıl yapılır: Tasarımcıyı kullanarak ClickOnce uygulamalarında URL etkinleştirmeyi devre dışı bırakma
Genellikle bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama, bir Web sunucusundan yüklendikten hemen sonra otomatik olarak başlatılır. Güvenlik nedenleriyle, bu davranışı devre dışı bırakmayı ve kullanıcılara bunun yerine **Başlangıç** menüsünden uygulamayı başlatmasını söylemeniz gerekebilir. Aşağıdaki yordamda URL etkinleştirmeyi devre dışı bırakma açıklanmaktadır.

 Bu teknik, yalnızca [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kullanıcının bilgisayarında bir Web sunucusundan yüklenen uygulamalar için kullanılabilir. Yalnızca kendi URL 'SI kullanılarak başlatılabilen, yalnızca çevrimiçi uygulamalar için kullanılamaz. Yalnızca çevrimiçi ve yüklü uygulamalar arasındaki fark hakkında daha fazla bilgi için bkz. [ClickOnce dağıtım stratejisi seçme](../deployment/choosing-a-clickonce-deployment-strategy.md).

 Bu yordam kullanır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Ayrıca, kullanarak bu görevi gerçekleştirebilirsiniz [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . Daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce UYGULAMALARıNıN URL etkinleştirmeyi devre dışı bırakma](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).

## <a name="procedure"></a>Yordam

#### <a name="to-disable-url-activation-for-your-application"></a>Uygulamanız için URL etkinleştirmeyi devre dışı bırakmak için

1. **Çözüm Gezgini** ' de proje adına sağ tıklayın ve **Özellikler** ' e tıklayın.

2. **Özellikler** sayfasında, **Yayımla** sekmesine tıklayın.

3. **Seçenekler** ’e tıklayın.

4. **Bildirimler** ' e tıklayın.

5. **Uygulamanın BIR URL aracılığıyla etkinleştirilmesini engelle** etiketli onay kutusunu seçin.

6. Uygulamanızı dağıtın.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)