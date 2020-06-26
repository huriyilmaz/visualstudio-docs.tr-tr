---
title: ClickOnce uygulaması için bir güvenlik bölgesi ayarlama | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51515339c24ea8a0507c47d0399cde9e423f71a0
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382139"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Nasıl yapılır: ClickOnce uygulaması için güvenlik bölgesi ayarlama
ClickOnce uygulaması için kod erişimi güvenlik izinlerini ayarlarken, **Proje Tasarımcısı**'nın **güvenlik** sayfasında bir temel izin kümesiyle başlamanız gerekir.

 Çoğu durumda, sınırlı bir izin kümesi içeren **Internet** bölgesini veya daha büyük bir izin kümesi Içeren **Yerel Intranet** bölgesini de seçebilirsiniz. Uygulamanız özel izinler gerektiriyorsa, **özel** güvenlik bölgesini seçerek bunu yapabilirsiniz. Özel izinleri ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir ClickOnce uygulaması Için özel Izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

### <a name="to-set-a-security-zone"></a>Bir güvenlik bölgesi ayarlamak için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Güvenlik** sekmesine tıklayın.

3. **ClickOnce güvenlik ayarlarını etkinleştir** onay kutusunu seçin.

4. **Bu bir kısmi güven uygulaması** seçenek düğmesini seçin.

     **ClickOnce güvenlik izinleri** bölümündeki denetimler etkindir.

5. **Uygulamanızın yükleneceği bölgede** , açılan listeden bir güvenlik bölgesi seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: ClickOnce uygulaması için özel izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)
