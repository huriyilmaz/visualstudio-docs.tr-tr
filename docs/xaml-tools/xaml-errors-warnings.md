---
title: XAML hataları ve uyarıları
description: hataların nasıl sınıflandırıldığından, hata bilgilerinin nasıl alınacağı ve bunları düzeltme seçeneklerinin nasıl bulunacağı dahil olmak üzere Visual Studio XAML hataları ve uyarıları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 03/06/2018
ms.topic: error-reference
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.workload:
- multiple
ms.openlocfilehash: 01dd2befec3f531609206bbd848e534ade251597041bef1ab755a618cc72f1b0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121365098"
---
# <a name="xaml-errors-and-warnings"></a>XAML hataları ve uyarıları

XAML yazarken Visual Studio kodu siz yazarken analiz eder. Bir hata algılandığında kod satırında dalgalı bir çizgi görünür. Dalgalı çizgi üzerine gelindiğinde, hata veya uyarı hakkında daha fazla bilgi verilmektedir. Bazı hatalar ve uyarılar için hızlı bir eylem ampul görüntülenir ve **CTRL tuşunu** kullanarak + **.** klavye kısayolu, sorunu gidermeye yönelik seçenekleri görüntüler.

## <a name="error-types"></a>Hata türleri

Arka planda, birden çok araç XAML 'yi paralel olarak analiz eder. XAML hataları, hatayı algılayan araca bağlı olarak aşağıdaki üç türden birine kategorize edilir:

|**Hata algılanan**|**Hata kodu biçimi**|**Visual Studio Sürüm**|
| - |-----------------| - |
|XAML dil hizmeti (XAML Düzenleyicisi)|XLSxxxx| Tüm sürümler |
|XAML Tasarımcısı|XDGxxxx| Tüm sürümler | 
|XAML Düzenleme ve Devam Etme|XECxxxx| Visual Studio 2019 sürüm 16,1 veya öncesi |
|XAML Çalışırken Yeniden Yükleme | XHRxxxx | Visual Studio 2019 sürüm 16,2 veya üzeri |

XAML düzenleme işleminin yeniden markası hakkında daha fazla ayrıntı için & XAML Hot Reload olarak devam edin. [Sürüm notlarımıza](/visualstudio/releases/2019/release-notes-v16.2#wpfuwp-tooling) bakın

> [!Note]
> Tüm hatalar veya uyarıların karşılık gelen bir kodu yoktur. Bu hatalar genellikle XAML Tasarımcısı hatalardır.

## <a name="suppress-xaml-designer-errors"></a>XAML Tasarımcısı hatalarını gösterme

**Araçlar > seçenekler**' i seçerek **Seçenekler** iletişim kutusunu açın ve **> xaml > çeşitli metin düzenleyici**' yi seçin.

**XAML Tasarımcısı tarafından algılanan hataları göster** onay kutusunun işaretini kaldırın.

![XAML Tasarımcısı hatalarını gösterme](media/suppress_xaml_designer_errors.png)