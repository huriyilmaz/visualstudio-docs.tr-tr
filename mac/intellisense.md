---
title: IntelliSense
description: Mac için Visual Studio 'da IntelliSense kullanma hakkında bilgi
author: cobey
ms.author: cobey
ms.date: 08/16/2019
ms.openlocfilehash: 07ef1d6292e4ac88ca616d0f35e3fd831cacc649
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75405815"
---
# <a name="intellisense"></a>IntelliSense

IntelliSense, kod yazma ve düzenlemenin deneyiminden artırılmasına yardımcı olmak için çeşitli özellikler sağlar. Örneğin, kod tamamlanmasına ek olarak, IntelliSense altyapısı üye listeleri, parametre bilgileri ve hızlı bilgi bilgileri de sağlar.

Mac için Visual Studio, IntelliSense çekirdek Düzenleyici hizmeti tarafından sağlanır ve C#, XAML, F#, JavaScript gibi birçok dilde desteklenir. Mac için Visual Studio, henüz projeye aktarılmamış kitaplıkların tamamlanmalarından gösterilmesinin yanı sıra gelişmiş IntelliSense özelliklerine de sahiptir.

## <a name="code-completion"></a>Kod tamamlama

C# Kod dosyası gibi desteklenen bir dosya içine yazarken, şu anda yazmakta olduğunuz dize için geçerli tamamlama işlemleri bir tamamlanma listesinde görüntülenir ve siz yazarken güncelleştirilir. Ayrıca, metni silerseniz, liste otomatik olarak, verilen dizeyi tamamlamaya yönelik daha geniş olanaklar aralığını içerecek şekilde otomatik olarak güncelleştirilecek. 

Tamamlama penceresi ayrıca tür tarafından dahil edilen tamamlamaların filtrelenmesi için destek sağlar. Örneğin, Liste üyelerini yalnızca sınıflar veya temsilciler gibi türleri temsil edecek şekilde sınırlamak mümkündür. Bu filtreleme işlemi, filtrelemeye veya belirli bir türe karşılık gelen klavye kısayollarına göre süzülecek belirli bir simgeye tıklanınca etkinleştirilebilir. Tamamlama penceresinin alt kısmında bulunan simgeler aşağıdaki gibidir:

| Simge                         | Name          | Anahtar sözcüğü    | Kısayol tuşu |
| -----------------------------|---------------| -----------|--------|
| ![Sınıflar simgesi](media/classes-icon.png)  | sınıf         | `class`    |  ⌥ C
| ![Sabit simgesi](media/constant-icon.png) | sabiti      | `const`    |  ⌥ O
| ![Temsilci simgesi](media/delegate-icon.png) | temsilci      | `delegate` |  ⌥ D
| ![Sabit Listesi simgesi](media/enums-icon.png)    | enum          | `enum`     |  ⌥ E
| ![Olay simgesi](media/event-icon.png)    | olay         |            |  ⌥ V
| ![Alan simgesi](media/fields-icon.png)   | alan         |            |  ⌥ F
| ![Arabirim simgesi](media/interface-icon.png)| arabirim     | `interface`|  ⌥ I
| ![Anahtar sözcük simgesi](media/keyword-icon.png)  | sözcükle       |            |  ⌥ K
| ![Yöntem simgesi](media/method-icon.png)   | {1&gt; yöntemi&lt;1}        |            |  ⌥
| ![Ad alanı simgesi](media/namespace-icon.png)| ad alanı     | `namespace`|  ⌥ N
| ![Props simgesi](media/props-icon.png)    | özellik      |            |  ⌥ P
| ![Kod parçacığı simgesi](media/snippet-icon.png)  | gösterildiği       | `class`    |  ⌥ S
| ![Struct simgesi](media/struct-icon.png)   | Yapı     | `struct`   |  ⌥ S

Simgelere tıklayarak veya ilgili kısayol tuşlarına basarak, tamamlanma listesi yalnızca filtre kümesi tarafından tanımlanan türlerle sınırlayacaktır.  

![IntelliSense tür filtrelemesi](media/intellisense-typefiltering.gif)

## <a name="parameter-window"></a>Parametre penceresi

IntelliSense 'in başka bir özelliği, uygun yerlerde bir parametre listesi sağlayabilmesidir. Parametre listesi, Çağrılmakta olan kod için yöntem imzalarının ayrıntılarını sağlar. İmza içindeki yukarı/aşağı oklara tıklayarak, gereksinimlerinize en uygun olanını belirleyebilmek için kullanılabilir her bir parametre imzasının her biri boyunca geçiş yapabilirsiniz. İzin verilen veri türlerinin ayrıntılarına ek olarak, XML açıklamaları aracılığıyla hedef yöntemde tanımlanan bir açıklama da olabilir.

![Parametre Listesi](media/intellisense-parameter.png)

Parametreleri doldurduktan sonra, şu anda düzenlemekte olduğunuz parametre kalın olacaktır, ancak etkin olmayan parametreler standart ağırlığa sahip olur. 


## <a name="triggering-completion-window-and-parameter-window"></a>Tamamlama penceresi ve parametre penceresi tetikleniyor

Tamamlanma penceresi, kaynak dosyanız içine yazarken otomatik olarak tetiklenecektir. Ancak, `control-space`kısayolunu kullanarak tamamlama penceresini de tetikleyebilirsiniz. Bu anahtar birleşimi, tamamlanma listesinin giriş işaretinin geçerli konumunda görünmesine neden olur. 

Ayrıca, `control-shift-space`yazarak parametre penceresinin görünümünü el ile de tetikleyebilirsiniz. Giriş işareti bir parametre listesi için geçerli olan konumda olduğunda, parametre listesi, giriş işareti konumunun yakınında görünür.

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı eylemler (Windows üzerinde Visual Studio)](/visualstudio/ide/quick-actions)
- [Kodu yeniden düzenleme (Windows üzerinde Visual Studio)](/visualstudio/ide/refactoring-in-visual-studio)
