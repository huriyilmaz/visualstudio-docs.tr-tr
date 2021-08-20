---
title: Yayımlama sürümünü ClickOnce artırma
description: ClickOnce kullanarak düzeltme numarasının otomatik olarak artırımının ClickOnce kullanmayı Visual Studio.
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
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: c2f4db86a97743d8844ef7664d31cdf3649a14c7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127993"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Nasıl yapılır: Yayımlama sürümünü ClickOnce olarak artırma

Bir uygulamayı [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yayımlarken `Publish Version` özelliğinin değiştirilmesi, uygulamanın güncelleştirme olarak yayımlanır. Varsayılan olarak Visual Studio, uygulamayı her `Revision` yayımlarken `Publish Version` sayısını otomatik olarak artırır.

Bu davranışı, Project **Tasarımcısı'nın** **Yayımla sayfasında devre dışı leyebilirsiniz.**

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünde İçeri ve Dışarı  **Ayarlar'yi** seçin. Daha fazla bilgi için [bkz. Ayarları sıfırlama.](../ide/environment-settings.md#reset-settings)

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>Yayımlama sürümünü otomatik olarak artırmayı devre dışı bırakmak için

1. içinde bir proje **seçiliyken Çözüm Gezgini** menüsünde **Project'a** **tıklayın.**

2. Yayımla **sekmesine** tıklayın.

3. Sürümü **Yayımla bölümünde** Düzeltmeyi her **sürümle otomatik olarak artır onay kutusunun** işaretini kaldırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl ClickOnce: ClickOnce ayarlama](../deployment/how-to-set-the-clickonce-publish-version.md)
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl ClickOnce: ClickOnce Sihirbazı'nı kullanarak bir uygulama yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)