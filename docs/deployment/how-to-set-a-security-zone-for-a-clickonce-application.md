---
title: Güvenlik bölgesi ayarlama (ClickOnce uygulama)
description: ClickOnce Designer'daki temel izin kümesiyle başlayan bir ClickOnce uygulama için kod erişimi güvenlik izinlerini ayarlama hakkında Project öğrenin.
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
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Nasıl ClickOnce uygulama için güvenlik bölgesi ayarlama
ClickOnce uygulaması için kod erişimi güvenlik izinlerini ayarlarken, Project Tasarımcısı'nın **Güvenlik** sayfasındaki temel izin **kümesiyle başlamanız gerekir.**

 Çoğu durumda, sınırlı bir izin kümesi içeren **İnternet** bölgesi veya daha fazla izin kümesi içeren Yerel **intranet** bölgesi de seçebilirsiniz. Uygulamanıza özel izinler gerekiyorsa, Özel güvenlik bölgesi **seçerek bunu** yapabiliriz. Özel izinler ayarlama hakkında daha fazla bilgi için, [bkz. How to: Set Custom Permissions for a ClickOnce Application](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

### <a name="to-set-a-security-zone"></a>Bir güvenlik bölgesi ayarlamak için

1. içinde bir proje **seçiliyken Çözüm Gezgini** menüsünde **özellikler'Project** **tıklayın.**

2. **Güvenlik** sekmesine tıklayın.

3. ClickOnce **Security Ayarlar** onay kutusunu seçin.

4. Bu kısmi **bir güven uygulaması seçeneği düğmesini** seçin.

     Güvenlik izinleri bölümündeki **ClickOnce etkindir.**

5. Açılan **listeden, uygulamanın yükln** olduğu bölge'de bir güvenlik bölgesi seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl ClickOnce uygulama için özel izinler ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)
