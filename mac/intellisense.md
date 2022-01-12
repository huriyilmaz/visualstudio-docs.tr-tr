---
title: IntelliSense
description: Mac için Visual Studio 'da ıntellisense kullanma hakkında bilgi
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 08/16/2019
ms.topic: reference
ms.openlocfilehash: 4d33a75eb2f6e45d5768f3b1820c4de70146734e
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135804889"
---
# <a name="intellisense"></a>IntelliSense

IntelliSense, kod yazma ve düzenlemenin deneyiminden artırılmasına yardımcı olmak için çeşitli özellikler sağlar. Örneğin, kod tamamlanmasına ek olarak, IntelliSense altyapısı üye listeleri, parametre bilgileri ve hızlı bilgi bilgileri de sağlar.

Mac için Visual Studio, ıntellisense çekirdek düzenleyici hizmeti tarafından sağlanır ve C#, XAML, F #, JavaScript gibi birçok dilde desteklenir. Mac için Visual Studio, henüz projeye aktarılmamış kitaplıkların tamamlanmalarından gösterilmesinin yanı sıra gelişmiş ıntellisense özelliklerine de sahiptir.

## <a name="code-completion"></a>Kod tamamlama

C# kod dosyası gibi desteklenen bir dosya içine yazarken, şu anda yazmakta olduğunuz dize için geçerli tamamlama işlemleri bir tamamlanma listesinde görüntülenir ve siz yazarken güncelleştirilir. Ayrıca, metni silerseniz, liste otomatik olarak, verilen dizeyi tamamlamaya yönelik daha geniş olanaklar aralığını içerecek şekilde otomatik olarak güncelleştirilecek. 

Tamamlama penceresi ayrıca tür tarafından dahil edilen tamamlamaların filtrelenmesi için destek sağlar. Örneğin, Liste üyelerini yalnızca sınıflar veya temsilciler gibi türleri temsil edecek şekilde sınırlamak mümkündür. Bu filtreleme işlemi, filtrelemeye veya belirli bir türe karşılık gelen klavye kısayollarına göre süzülecek belirli bir simgeye tıklanınca etkinleştirilebilir. Tamamlama penceresinin alt kısmında bulunan simgeler aşağıdaki gibidir:

| Simge                         | Name          | Sözcükle    | Kısayol tuşu |
| -----------------------------|---------------| -----------|--------|
| ![Sınıflar simgesi](media/classes-icon.png)  | sınıf         | `class`    |  ⌥ C
| ![Sabit simgesi](media/constant-icon.png) |  sabiti      | `const`    |  ⌥ O
| ![Temsilci simgesi](media/delegate-icon.png) | temsilci      | `delegate` |  ⌥ D
| ![Sabit Listesi simgesi](media/enums-icon.png)    | enum          | `enum`     |  ⌥ E
| ![Olay simgesi](media/event-icon.png)    | event         |            |  ⌥ V
| ![Alan simgesi](media/fields-icon.png)   | alan         |            |  ⌥ F
| ![Arabirim simgesi](media/interface-icon.png)| arabirim     | `interface`|  ⌥ I
| ![Anahtar sözcük simgesi](media/keyword-icon.png)  | sözcükle       |            |  ⌥ K
| ![Yöntem simgesi](media/method-icon.png)   | method        |            |  ⌥
| ![Ad alanı simgesi](media/namespace-icon.png)| ad alanı     | `namespace`|  ⌥ N
| ![Props simgesi](media/props-icon.png)    | özellik      |            |  ⌥ P
| ![Kod parçacığı simgesi](media/snippet-icon.png)  | gösterildiği       | `class`    |  ⌥ S
| ![Struct simgesi](media/struct-icon.png)   | yapı     | `struct`   |  ⌥ S

Simgelere tıklayarak veya ilgili kısayol tuşlarına basarak, tamamlanma listesi yalnızca filtre kümesi tarafından tanımlanan türlerle sınırlayacaktır.  

![IntelliSense tür filtrelemesi](media/intellisense-typefiltering.gif)

## <a name="parameter-window"></a>Parametre penceresi

IntelliSense 'in başka bir özelliği, uygun yerlerde bir parametre listesi sağlayabilmesidir. Parametre listesi, Çağrılmakta olan kod için yöntem imzalarının ayrıntılarını sağlar. İmza içindeki yukarı/aşağı oklara tıklayarak, gereksinimlerinize en uygun olanını belirleyebilmek için kullanılabilir her bir parametre imzasının her biri boyunca geçiş yapabilirsiniz. İzin verilen veri türlerinin ayrıntılarına ek olarak, XML açıklamaları aracılığıyla hedef yöntemde tanımlanan bir açıklama da olabilir.

![Parametre Listesi](media/intellisense-parameter.png)

Parametreleri doldurduktan sonra, şu anda düzenlemekte olduğunuz parametre kalın olacaktır, ancak etkin olmayan parametreler standart ağırlığa sahip olur. 


## <a name="triggering-completion-window-and-parameter-window"></a>Tamamlama penceresi ve parametre penceresi tetikleniyor

Tamamlanma penceresi, kaynak dosyanız içine yazarken otomatik olarak tetiklenecektir. Ancak, kısayolu kullanarak tamamlama penceresini de tetikleyebilirsiniz `control-space` . Bu anahtar birleşimi, tamamlanma listesinin giriş işaretinin geçerli konumunda görünmesine neden olur. 

Ayrıca, yazarak parametre penceresinin görünümünü el ile de tetikleyebilirsiniz `control-shift-space` . Giriş işareti bir parametre listesi için geçerli olan konumda olduğunda, parametre listesi, giriş işareti konumunun yakınında görünür.

## <a name="see-also"></a>Ayrıca bkz.

- [hızlı eylemler (Windows Visual Studio)](/visualstudio/ide/quick-actions)
- [kodu yeniden düzenleme (Windows Visual Studio)](/visualstudio/ide/refactoring-in-visual-studio)
