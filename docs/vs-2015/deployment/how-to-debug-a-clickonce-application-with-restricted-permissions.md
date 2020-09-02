---
title: 'Nasıl yapılır: kısıtlanmış Izinlerle ClickOnce uygulamasında hata ayıklama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d60f88c4d1532a03922f12f21bb9b455ef5d84d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153793"
---
# <a name="how-to-debug-a-clickonce-application-with-restricted-permissions"></a>Nasıl yapılır: Sınırlı İzinler ile ClickOnce Uygulamasında Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ClickOnce uygulaması için özel Izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md)   
 [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce Uygulamalarının Güvenliğini Sağlama](../deployment/securing-clickonce-applications.md)
