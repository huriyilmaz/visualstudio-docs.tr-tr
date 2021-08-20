---
title: Uygulama için yayımlama dilini ClickOnce değiştirme
description: Geliştirme bilgisayarınızın dilini/kültürünü varsayılan olarak belirlemek ClickOnce yerelleştirme uygulaması için dil/kültür belirtmeyi öğrenin.
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
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 4e34b5a28df05758eb24d6af2c907e99d0f9b9f7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160841"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Nasıl ClickOnce uygulama için yayımlama dilini değiştirme

Bir uygulamayı [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yayımlarken, yükleme sırasında görüntülenen kullanıcı arabirimi varsayılan olarak geliştirme bilgisayarınızın dilini ve kültürünü kullanır. Yerelleştirilmiş bir uygulama yayımlarsanız, yerelleştirilmiş sürümle eşleşmesi için bir dil ve kültür belirtmeniz gerekir. Bu, projenizin `Publish language` özelliği tarafından belirlenir.

özelliği, `Publish language` Yayımlama Seçenekleri iletişim **kutusunda,** Project **Tasarımcısı'nın** Yayımla **sayfasından erişilebilir.**

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünde İçeri ve Dışarı  **Ayarlar'yi** seçin. Daha fazla bilgi için [bkz. Ayarları sıfırlama.](../ide/environment-settings.md#reset-settings)

## <a name="to-change-the-publish-language"></a>Yayımlama dilini değiştirmek için

1. içinde bir proje **seçiliyken Çözüm Gezgini** menüsünde **Project'a** **tıklayın.**

2. Yayımla **sekmesine** tıklayın.

3. Seçenekleri **Yayımla** iletişim kutusunu açmak **için Seçenekler düğmesine** tıklayın.

4. **Açıklama'ya tıklayın.**

5. Yayımlama **Seçenekleri iletişim** kutusunda, Dili yayımla açılan listesinden bir dil **ve** kültür seçin ve ardından Tamam'a **tıklayın.**

## <a name="see-also"></a>Ayrıca bkz.

- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl ClickOnce: ClickOnce Sihirbazı'nı kullanarak bir uygulama yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)