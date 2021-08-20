---
title: tasarımcı kullanarak ClickOnce uygulamalarının URL etkinleştirmeyi devre dışı bırakma
description: kullanıcıların uygulamayı Başlat menüsü başlatması için Visual Studio kullanarak ClickOnce bir uygulama için yüklemenin otomatik olarak nasıl devre dışı bırakılacağını öğrenin.
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: b86b9ecd4ada8396f603af2555de11efd7d3c51e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160666"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>nasıl yapılır: tasarımcıyı kullanarak ClickOnce uygulamalarının URL etkinleştirmeyi devre dışı bırakma
Genellikle bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama, bir Web sunucusundan yüklendikten hemen sonra otomatik olarak başlatılır. Güvenlik nedenleriyle, bu davranışı devre dışı bırakmayı ve kullanıcılara bunun yerine **Başlangıç** menüsünden uygulamayı başlatmasını söylemeniz gerekebilir. Aşağıdaki yordamda URL etkinleştirmeyi devre dışı bırakma açıklanmaktadır.

 Bu teknik, yalnızca [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kullanıcının bilgisayarında bir Web sunucusundan yüklenen uygulamalar için kullanılabilir. Yalnızca kendi URL 'SI kullanılarak başlatılabilen, yalnızca çevrimiçi uygulamalar için kullanılamaz. yalnızca çevrimiçi ve yüklü uygulamalar arasındaki fark hakkında daha fazla bilgi için bkz. [ClickOnce dağıtım stratejisi seçme](../deployment/choosing-a-clickonce-deployment-strategy.md).

 Bu yordam kullanır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Ayrıca, kullanarak bu görevi gerçekleştirebilirsiniz [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce uygulamaların URL etkinleştirmeyi devre dışı bırakma](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).

## <a name="procedure"></a>Yordam

#### <a name="to-disable-url-activation-for-your-application"></a>Uygulamanız için URL etkinleştirmeyi devre dışı bırakmak için

1. **Çözüm Gezgini**' de proje adına sağ tıklayın ve **Özellikler**' e tıklayın.

2. **Özellikler** sayfasında, **Yayımla** sekmesine tıklayın.

3. **Seçenekler**’e tıklayın.

4. **Bildirimler**' e tıklayın.

5. **Uygulamanın BIR URL aracılığıyla etkinleştirilmesini engelle** etiketli onay kutusunu seçin.

6. Uygulamanızı dağıtın.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)