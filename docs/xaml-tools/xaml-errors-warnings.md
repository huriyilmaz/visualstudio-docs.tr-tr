---
title: XAML Hataları ve Uyarıları
ms.date: 03/06/2018
ms.topic: conceptual
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: karann-msft
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8a36a91f40fd4857e50d5262c1598ee096697e7
ms.sourcegitcommit: 22deb247ad951e4971f27fdab413b158415d0584
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81276468"
---
# <a name="xaml-errors-and-warnings"></a>XAML hataları ve uyarıları

XAML yazarken, Visual Studio yazarken kodu analiz eder. Bir hata algılandığında kod satırında bir kıvrım görüntülenir. Dalgalı üzerinde gezinme hata veya uyarı hakkında daha fazla bilgi verir. Bazı hatalar ve uyarılar için, bir Hızlı Eylem ampul görüntülenir ve **Ctrl**+kullanılarak **.** klavye kısayolu sorunu gidermek için seçenekleri görüntüler.

## <a name="error-types"></a>Hata türleri

Arka planda, birden çok araç XAML'yi paralel olarak analiz edeyim. XAML hataları, hatayı algılayan araca göre aşağıdaki üç türden birine ayrılır:

|**Tarafından algılanan hata**|**Hata kodu biçimi**|
| - |-----------------|
|XAML Dil Servisi (XAML editörü)|XLSxxxx|
|XAML Tasarımcısı|XDGxxxx|
|XAML'yi Edit ve Devam Et|XECxxxx|

> [!Note]
> Tüm hatalar veya uyarılar karşılık gelen bir kod var. Bu tür hatalar genellikle XAML Designer hatalarıdır.

## <a name="suppress-xaml-designer-errors"></a>XAML Tasarımcı hatalarını bastırma

**Araçlar > Seçenekleri'ni**seçerek **Seçenekler** iletişim kutusunu açın ve ardından **XAML > Çeşitli > Metin**Düzenleyicisi'ni seçin.

XAML tasarımcı onay kutusu **tarafından algılanan hataları göster'in denetimini** kaldırın.

![XAML Tasarımcı hatalarını bastırma](media/suppress_xaml_designer_errors.png)
