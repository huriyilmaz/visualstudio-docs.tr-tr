---
title: Kısıtlanmış izinlerle ClickOnce uygulamasında hata ayıklama
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ClickOnce applications
- ClickOnce deployment, debugging
- ClickOnce applications, debugging
ms.assetid: 6991ea91-5253-451b-923d-22273a3d38b1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d942c41aac873b775566efa4e128651a8830e92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727959"
---
# <a name="how-to-debug-a-clickonce-application-with-restricted-permissions"></a>Nasıl yapılır: kısıtlanmış izinlerle ClickOnce uygulamasında hata ayıklama
Bir geliştirici olarak, büyük olasılıkla geliştirme bilgisayarınızı tam güven izinleriyle çalıştırıyorsunuz, bu nedenle, son kullanıcının kısıtlanmış izinlerle çalışırken görebileceği bir ClickOnce uygulamasında hata ayıklarken aynı güvenlik özel durumlarını görmeyecektir.

 Bu özel durumları yakalamak için, son kullanıcıyla aynı izinlerle uygulamada hata ayıklaması yapmanız gerekir. Kısıtlanmış izinlerle hata ayıklama, **Proje Tasarımcısı**'nın **güvenlik** sayfasında etkinleştirilebilir.

 Ayrıca, Web Hizmetleri 'ni çağıran uygulamalar geliştirirken, bu Web Hizmetleri genellikle geliştirme bilgisayarınızda bulunur. Dağıtım yapıldıktan sonra, Son Kullanıcı bu Web hizmetlerine farklı bir URL 'den erişir. Hata ayıklama sırasında son kullanıcı deneyimine benzemek için bir URL belirtebilirsiniz ve hata ayıklayıcı Web hizmetlerini bu URL 'den çağrılmış gibi değerlendirir.

### <a name="to-enable-debugging-with-restricted-permissions"></a>Kısıtlanmış izinlerle hata ayıklamayı etkinleştirmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Proje tasarımcısında** **güvenlik** sekmesine tıklayın.

3. **ClickOnce güvenlik ayarını etkinleştir** onay kutusunu işaretleyin ve ardından **Bu kısmi güven uygulaması** seçenek düğmesine tıklayın.

4. **Gelişmiş** düğmesine tıklayın.

5. **Bu uygulamayı seçili izin kümesiyle hata ayıkla** onay kutusunu seçin ve ardından **Tamam**' a tıklayın.

     Uygulamada hata ayıklarken, izin kümesinin bir parçası olmayan bir izne erişim girişimleri bir güvenlik özel durumu oluşturacak.

### <a name="to-specify-a-url-for-debugging"></a>Hata ayıklama için bir URL belirtmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Proje tasarımcısında** **güvenlik** sekmesine tıklayın.

3. **ClickOnce güvenlik ayarını etkinleştir** onay kutusunu işaretleyin ve ardından **Bu kısmi güven uygulaması** seçenek düğmesine tıklayın.

4. **Gelişmiş** düğmesine tıklayın.

5. **Bu uygulamayı seçili izin kümesiyle hata ayıkla** onay kutusunu seçin ve ardından **Tamam**' a tıklayın.

6. **AŞAĞıDAKI URL 'den indirilmiş gibi bu uygulamada hata ayıkla** metin kutusuna bir URL veya ağ yolu girin.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: ClickOnce uygulaması için özel izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Güvenli ClickOnce uygulamaları](../deployment/securing-clickonce-applications.md)
- [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)
- [Güvenli ClickOnce uygulamaları](../deployment/securing-clickonce-applications.md)