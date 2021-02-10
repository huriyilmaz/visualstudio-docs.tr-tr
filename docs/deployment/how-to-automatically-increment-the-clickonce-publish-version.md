---
title: ClickOnce yayımlama sürümünü otomatik artırma
description: Visual Studio 'Yu kullanarak ClickOnce uygulamanız için düzeltme numarasının otomatik olarak arttırılini nasıl devre dışı bırakacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b84b0a8932bb9d8fd4738c2cd4924b61bb6faeb7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947781"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Nasıl yapılır: ClickOnce Yayım sürümünü otomatik olarak artırma

Bir uygulamayı yayımlarken [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , `Publish Version` özelliği değiştirmek uygulamanın bir güncelleştirme olarak yayımlanmasına neden olur. Varsayılan olarak, Visual Studio `Revision` `Publish Version` uygulamayı her yayımlaışınızda otomatik olarak sayısını artırır.

Bu davranışı **Proje Tasarımcısı**' nın **Yayımla** sayfasında devre dışı bırakabilirsiniz.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [ayarları sıfırlama](../ide/environment-settings.md#reset-settings).

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>Yayımlama sürümünü otomatik olarak arttırmadan devre dışı bırakmak için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Sürümü Yayımla** bölümünde, **her sürüm Için düzeltmeyi otomatik olarak artır** onay kutusunu temizleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: ClickOnce yayımlama sürümünü ayarlama](../deployment/how-to-set-the-clickonce-publish-version.md)
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)