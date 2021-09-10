---
title: IntelliSense
description: Mac için Visual Studio'de IntelliSense kullanma hakkında Mac için Visual Studio
author: cobey
ms.author: cobey
ms.date: 08/16/2019
ms.openlocfilehash: 07ef1d6292e4ac88ca616d0f35e3fd831cacc649
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964799"
---
# <a name="intellisense"></a>IntelliSense

IntelliSense, kod yazma ve düzenleme deneyimini geliştirmeye yardımcı olan çeşitli özellikler sağlar. Örneğin, Kod tamamlamaya ek olarak IntelliSense altyapısı üye listeleri, parametre bilgileri ve hızlı bilgiler de sağlar.

Bu Mac için Visual Studio IntelliSense, temel düzenleyici hizmeti tarafından sağlanır ve C#, XAML, F#, JavaScript ve daha birçok dilde de sağlanır. Mac için Visual Studio henüz projeye aktarılmış kitaplıklardan tamamlamaları gösterme gibi gelişmiş IntelliSense özelliklerine de sahiptir.

## <a name="code-completion"></a>Kod Tamamlama

C# kod dosyası gibi desteklenen bir dosyanın içinde yazarken, yazdığınız dize için geçerli tamamlamalar bir tamamlama listesinde görüntülenir ve siz yazarken güncelleştirilir. Ayrıca, metni silersiniz, liste verilen dizeyi tamamlamak için daha geniş bir olasılık aralığını içerecek şekilde yeniden otomatik olarak güncelleştirmeyi de sağlar. 

Tamamlama penceresi, dahil edilen tamamlamaları türe göre filtreleme desteği de sunar. Örneğin, listenin üyelerini yalnızca sınıflar veya temsilciler gibi türleri temsil edecek şekilde sınırlamak mümkündür. Bu filtreleme işlemi, filtrelenmiş türü temsil eden belirli bir simgeye tıklar veya belirli bir türe karşılık gelen klavye kısayolları aracılığıyla etkinleştirilebilir. Tamamlama penceresinin en altında bulunan simgeler aşağıdaki gibidir:

| Simge                         | Name          | Anahtar kelime    | Hotkey |
| -----------------------------|---------------| -----------|--------|
| ![Sınıflar Simgesi](media/classes-icon.png)  | sınıf         | `class`    |  ⌥C
| ![Sabit Simgesi](media/constant-icon.png) |  sabiti      | `const`    |  ⌥O
| ![Temsilci Simgesi](media/delegate-icon.png) | temsilci      | `delegate` |  ⌥D
| ![Enum simgesi](media/enums-icon.png)    | enum          | `enum`     |  ⌥E
| ![Olay Simgesi](media/event-icon.png)    | event         |            |  ⌥V
| ![Alan Simgesi](media/fields-icon.png)   | alan         |            |  ⌥F
| ![Arabirim Simgesi](media/interface-icon.png)| arabirim     | `interface`|  ⌥I
| ![Anahtar Sözcük Simgesi](media/keyword-icon.png)  | Anahtar kelime       |            |  ⌥K
| ![Yöntem Simgesi](media/method-icon.png)   | method        |            |  ⌥M
| ![Ad Alanı Simgesi](media/namespace-icon.png)| ad alanı     | `namespace`|  ⌥N
| ![Props Simgesi](media/props-icon.png)    | özellik      |            |  ⌥P
| ![Kod Parçacığı Simgesi](media/snippet-icon.png)  | Parçacığını       | `class`    |  ⌥S
| ![Yapı Simgesi](media/struct-icon.png)   | yapı     | `struct`   |  ⌥S

Simgelerden herhangi bir simgeye tıklayarak veya ilgili kısayol tuşlarına basarak tamamlama listesi yalnızca filtre kümesi tarafından tanımlanan türlerle sınırlayıcı olur.  

![Intellisense Tür Filtreleme](media/intellisense-typefiltering.gif)

## <a name="parameter-window"></a>Parametre Penceresi

IntelliSense'in bir diğer özelliği de uygun olduğunda parametre listesi sağlayabilme özelliğidir. Parametre listesi, çağrılan kod için yöntem imzalarının ayrıntılarını sağlar. İmzanın içindeki yukarı/aşağı oklara tıklayarak, kullanılabilir parametre imzalarının her biri arasında döngüye geçerek, ihtiyaçlarınıza en uygun olanı seçebilirsiniz. İzin verilen veri türlerinin ayrıntılarına ek olarak, XML açıklamaları aracılığıyla hedef yöntemde tanımlandığı gibi bir açıklama da olabilir.

![Parametre Listesi](media/intellisense-parameter.png)

Parametreleri doldururken şu anda düzenlemekte olan parametre kalın, etkin olmayan parametreler ise standart ağırlık değerine sahip olur. 


## <a name="triggering-completion-window-and-parameter-window"></a>Tamamlama Penceresini ve Parametre Penceresini Tetikleme

Siz kaynak dosyanıza yazarak tamamlama penceresi otomatik olarak tetiklenir. Ancak, kısayolunu kullanarak tamamlama penceresini de `control-space` tetiklersiniz. Bu tuş bileşimi tamamlama listesinin, noktanın geçerli konumunda görünmesine neden olur. 

Ayrıca, yazarak parametre penceresinin görünümünü el ile `control-shift-space` tetikleyebilirsiniz. Caret'iniz bir parametre listesi için geçerli konumda olduğunda parametre listesi, caret konumunun yakınında görünür.

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Eylemler (Visual Studio Windows)](/visualstudio/ide/quick-actions)
- [Kodu yeniden düzenleme (Visual Studio üzerinde Windows)](/visualstudio/ide/refactoring-in-visual-studio)
