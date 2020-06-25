---
title: XAML Hataları ve Uyarıları
ms.date: 03/06/2018
ms.topic: reference
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b46bf15390f12e7fb0873c7e4c39abf94530821
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330412"
---
# <a name="xaml-errors-and-warnings"></a>XAML hataları ve uyarıları

XAML yazarken, Visual Studio kodu yazarken analiz eder. Bir hata algılandığında kod satırında dalgalı bir çizgi görünür. Dalgalı çizgi üzerine gelindiğinde, hata veya uyarı hakkında daha fazla bilgi verilmektedir. Bazı hatalar ve uyarılar için hızlı bir eylem ampul görüntülenir ve **CTRL tuşunu**kullanarak + **.** klavye kısayolu, sorunu gidermeye yönelik seçenekleri görüntüler.

## <a name="error-types"></a>Hata türleri

Arka planda, birden çok araç XAML 'yi paralel olarak analiz eder. XAML hataları, hatayı algılayan araca bağlı olarak aşağıdaki üç türden birine kategorize edilir:

|**Hata algılanan**|**Hata kodu biçimi**|
| - |-----------------|
|XAML dil hizmeti (XAML Düzenleyicisi)|XLSxxxx|
|XAML Tasarımcısı|XDGxxxx|
|XAML Düzenle ve devam et|XECxxxx|

> [!Note]
> Tüm hatalar veya uyarıların karşılık gelen bir kodu yoktur. Bu hatalar genellikle XAML Tasarımcısı hatalardır.

## <a name="suppress-xaml-designer-errors"></a>XAML Tasarımcısı hatalarını gösterme

**Araçlar > seçenekler**' i seçerek **Seçenekler** iletişim kutusunu açın ve **> xaml > çeşitli metin düzenleyici**' yi seçin.

**XAML Tasarımcısı tarafından algılanan hataları göster** onay kutusunun işaretini kaldırın.

![XAML Tasarımcısı hatalarını gösterme](media/suppress_xaml_designer_errors.png)
