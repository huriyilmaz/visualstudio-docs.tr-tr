---
title: ClickOnce uygulaması için yayımlama dilini değiştirme
description: Geliştirme bilgisayarınızın dilini/kültürünü varsayılan olarak kullanmak yerine, ClickOnce 'ta yerelbir uygulama için bir dil/kültür belirtmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c0d9c3d49dde0bdef41e89ee71139fb1ab621297
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851471"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Nasıl yapılır: ClickOnce uygulaması için yayımlama dilini değiştirme

Bir uygulamayı yayımlarken [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , yükleme sırasında görüntülenecek kullanıcı arabirimi, geliştirme bilgisayarınızın diline ve kültürünü varsayılan olarak alır. Yerelleştirilmiş bir uygulama yayımlıyorsanız, yerelleştirilmiş sürümle eşleşecek bir dil ve kültür belirtmeniz gerekecektir. Bu, `Publish language` projeniz için özelliği tarafından belirlenir.

`Publish language`Özelliği, **Proje Tasarımcısı**' nın **Yayımla** sayfasından erişilebilen **Yayımla Seçenekleri** iletişim kutusunda ayarlanabilir.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [ayarları sıfırlama](../ide/environment-settings.md#reset-settings).

## <a name="to-change-the-publish-language"></a>Yayımla dilini değiştirmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Yayımla Seçenekleri** iletişim kutusunu açmak için **Seçenekler** düğmesine tıklayın.

4. **Açıklama**' ya tıklayın.

5. **Yayımla Seçenekleri** iletişim kutusunda, **yayınlama dili** açılır listesinden bir dil ve kültür seçin ve ardından **Tamam**' a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)