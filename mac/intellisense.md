---
title: IntelliSense
description: Mac için Visual Studio'da IntelliSense kullanma hakkında bilgi
author: cobey
ms.author: cobey
ms.date: 08/16/2019
ms.openlocfilehash: 07ef1d6292e4ac88ca616d0f35e3fd831cacc649
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75405815"
---
# <a name="intellisense"></a>IntelliSense

IntelliSense kod yazma ve düzenleme deneyimini geliştirmeye yardımcı olmak için çeşitli özellikler sağlar. Örneğin, kod tamamlamaya ek olarak, IntelliSense altyapısı üye listeleri, parametre bilgileri ve hızlı bilgi de sağlar.

Visual Studio for Mac'te IntelliSense çekirdek düzenleyici hizmeti tarafından sağlanır ve C#, XAML, F#, JavaScript ve daha fazlası gibi birçok dilde desteklenir. Mac için Visual Studio, henüz projeye alınmamış kitaplıklardan tamamlanmaları gösterme özelliği gibi gelişmiş IntelliSense özelliklerine de sahiptir.

## <a name="code-completion"></a>Kod Tamamlama

C# kodu dosyası gibi desteklenen bir dosya içinde yazarken, şu anda yazmakta olduğunuz dize için geçerli tamamlamalar bir tamamlama listesinde görüntülenir ve siz yazarken güncelleştirilir. Ayrıca, metni silerseniz, liste verilen dizeyi tamamlamak için daha geniş bir olasılık aralığını içerecek şekilde yeniden otomatik güncelleştirmeyi yeniden günceller. 

Tamamlama penceresi, dahil edilen tamamlanmaları türüne göre filtreleme desteği de sunar. Örneğin, liste üyelerini yalnızca sınıflar veya temsilciler gibi türleri temsil edecek şekilde sınırlamak mümkündür. Bu filtreleme işlemi, filtrelenecek türü temsil eden belirli bir simgeye tıklayarak veya belirli bir türe karşılık gelen klavye kısayollarından etkinleştirilebilir. Tamamlama penceresinin alt kısmında bulunan simgeler aşağıdaki gibidir:

| Simge                         | Adı          | Anahtar kelime    | Hotkey |
| -----------------------------|---------------| -----------|--------|
| ![Sınıflar Simgesi](media/classes-icon.png)  | sınıf         | `class`    |  2007'de 19
| ![Sabit Simge](media/constant-icon.png) |  sabiti      | `const`    |  O
| ![Temsilci Simgesi](media/delegate-icon.png) | temsilci      | `delegate` |  D
| ![Enum simgesi](media/enums-icon.png)    | enum          | `enum`     |  E-
| ![Etkinlik Simgesi](media/event-icon.png)    | event         |            |  1990'lı ve 1
| ![Alan Simgesi](media/fields-icon.png)   | alan         |            |  F
| ![Arayüz Simgesi](media/interface-icon.png)| arabirim     | `interface`|  I
| ![Anahtar Kelime Simgesi](media/keyword-icon.png)  | Anahtar kelime       |            |  10 000 000
| ![Yöntem Simgesi](media/method-icon.png)   | method        |            |  2007-201
| ![Ad Alanı Simgesi](media/namespace-icon.png)| ad alanı     | `namespace`|  1. N
| ![Sahne Simgesi](media/props-icon.png)    | özellik      |            |  100 000
| ![Parçacık Simgesi](media/snippet-icon.png)  | Parçacığını       | `class`    |  S
| ![Yapı Simgesi](media/struct-icon.png)   | yapı     | `struct`   |  S

Simgelerden herhangi birini tıklatarak veya ilgili kısayol tuşlarına basarak, tamamlanma listesi yalnızca filtre kümesi tarafından tanımlanan türlerle sınırlanır.  

![Intellisense Tipi Filtreleme](media/intellisense-typefiltering.gif)

## <a name="parameter-window"></a>Parametre Penceresi

IntelliSense'in bir diğer özelliği de uygun olduğunda parametre listesi sağlayabilmektir. Parametre listesi, çağrılan kod için yöntem imzalarının ayrıntılarını sağlar. İmzanın içindeki yukarı/aşağı oklara tıklayarak, gereksinimlerinize en uygun olanı belirlemek için mevcut parametre imzalarının her birini tıklatabilirsiniz. İzin verilen veri türlerinin ayrıntılarına ek olarak, XML yorumları aracılığıyla hedef yöntemde tanımlandığı gibi bir açıklama da olabilir.

![Parametre Listesi](media/intellisense-parameter.png)

Parametreleri doldurdukça, şu anda düzenlemekte olduğunuz parametre kalınlaşacak, etkin olmayan parametreler ise standart ağırlıkta olacaktır. 


## <a name="triggering-completion-window-and-parameter-window"></a>Tamamlama Penceresi ve Parametre Penceresi Tetikleme

Kaynak dosyanıza yazarken tamamlama penceresi otomatik olarak tetiklenir. Ancak, kısayolu `control-space`kullanarak tamamlama penceresini de tetikleyebilirsiniz. Bu anahtar kombinasyonu, tamamlanma listesinin caret'inizin geçerli konumunda görünmesine neden olur. 

Ayrıca parametre penceresinin görünümünü el ile yazarak `control-shift-space`tetikleyebilirsiniz. Caret'iniz parametre listesi için geçerli konumdayken, parametre listesi caret pozisyonunun yanında görünür.

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Eylemler (Windows'ta Visual Studio)](/visualstudio/ide/quick-actions)
- [Refactor kodu (Windows'ta Visual Studio)](/visualstudio/ide/refactoring-in-visual-studio)
