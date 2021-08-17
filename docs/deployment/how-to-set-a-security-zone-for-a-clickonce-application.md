---
title: güvenlik bölgesini ayarlama (ClickOnce uygulaması)
description: Project tasarımcısında temel bir izin kümesiyle başlayan ClickOnce bir uygulama için kod erişimi güvenlik izinlerini ayarlama hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, security settings
- code access security, ClickOnce applications
- security zones, ClickOnce applications
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 88654d1d115ee84a13d541e26e085f1acf5c03e031900dcc6ab12e67efcf0c7e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403873"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>nasıl yapılır: ClickOnce bir uygulama için güvenlik bölgesi ayarlama
ClickOnce bir uygulama için kod erişimi güvenlik izinlerini ayarlarken, **Project tasarımcısının** **güvenlik** sayfasında temel bir izin kümesiyle başlamanız gerekir.

 Çoğu durumda, sınırlı bir izin kümesi içeren **Internet** bölgesini veya daha büyük bir izin kümesi Içeren **Yerel Intranet** bölgesini de seçebilirsiniz. Uygulamanız özel izinler gerektiriyorsa, **özel** güvenlik bölgesini seçerek bunu yapabilirsiniz. özel izinleri ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: özel izinleri ayarlama ClickOnce uygulama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

### <a name="to-set-a-security-zone"></a>Bir güvenlik bölgesi ayarlamak için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Project** menüsünde **özellikler**' e tıklayın.

2. **Güvenlik** sekmesine tıklayın.

3. **ClickOnce güvenliği etkinleştir Ayarlar** onay kutusunu seçin.

4. **Bu bir kısmi güven uygulaması** seçenek düğmesini seçin.

     **ClickOnce güvenlik izinleri** bölümündeki denetimler etkinleştirilmiştir.

5. **Uygulamanızın yükleneceği bölgede** , açılan listeden bir güvenlik bölgesi seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [nasıl yapılır: bir ClickOnce uygulaması için özel izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)
