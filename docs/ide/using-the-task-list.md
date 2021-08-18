---
title: Görev Listesini Kullanma
description: Kod açıklamalarını Görev Listesi ve Visual Studio daha verimli bir şekilde nasıl kullanabileceğinizi öğrenin.
ms.date: 10/12/2020
ms.topic: how-to
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: c20f0b6eb2a496455469f3bc7404839954add74d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122116805"
---
# <a name="use-the-task-list"></a>Görev Listesini Kullanma

Ve **Görev Listesi** veya özel belirteçler kullanan kod açıklamalarını izlemek ve sizi doğrudan kodda önceden tanımlanmış bir konuma alan kısayolları yönetmek için bir uygulama `TODO` `HACK` kullanın. Kaynak kodda bulunduğu konuma gitmek için listede öğeye tıklayın.

> [!NOTE]
> Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio için [bkz. Görev yorumları (Mac için Visual Studio)](/visualstudio/mac/task-comments).

## <a name="the-task-list-window"></a>Görev Listesi penceresi

Görev Listesi  açık olduğunda, uygulama penceresinin alt kısmında görünür.

Bir Görev Listesi açmak **için**   >  **Görünüm'Görev Listesi 'ı** seçin veya klavyeden **Ctrl**, + **\\** **T tuşlarına basın.**

![Görev Listesi penceresi](../ide/media/vs2015_task_list.png)

Listenin sıralama sıralama sıralamalarını değiştirmek için herhangi bir sütunun üst bilgisini seçin. Arama sonuçlarınızı daha da geliştirmek için **Shift tuşuna basın** ve ikinci bir sütun başlığına tıklayın. Alternatif olarak, kısayol menüsünde Sıralamaya **göre'yi ve** ardından bir üst bilgi seçin. Arama sonuçlarınızı daha da geliştirmek için **Shift tuşuna basın** ve ikinci bir üst bilgi seçin.

Sütunları göstermek veya gizlemek için kısayol menüsünde Sütunları **Göster'i seçin.** Göstermek veya gizlemek istediğiniz sütunları seçin.

Sütunların sıralamalarını değiştirmek için herhangi bir sütun üst bilgisini istediğiniz konuma sürükleyin.

## <a name="user-tasks"></a>Kullanıcı görevleri

Kullanıcı görevi özelliği 2015'Visual Studio kaldırıldı. Visual Studio 2013 ve önceki sürümlerinden kullanıcı görev verilerine sahip bir çözüm asanız, *.suo* dosyanız içinde kullanıcı görev verileri etkilenmez, ancak kullanıcı görevleri görev listesinde görüntülenmez.

Kullanıcı görev verilerinize erişmeye ve verileri güncelleştirmeye devam etmek isterseniz projeyi Visual Studio 2013'de açın ve tüm kullanıcı görevlerinin içeriğini tercih ettiğiniz proje yönetim aracına (örneğin Team Foundation Server).

## <a name="tokens-and-comments"></a>Belirteçler ve açıklamalar

Kodunda önünde açıklama işaretçisi olan bir açıklama ve önceden tanımlanmış bir belirteç de **Görev Listesi.** Örneğin, aşağıdaki C# açıklamasının üç ayrı bölümü vardır:

- Açıklama işaretçisi ( `//` )

- Belirteç, örneğin ( `TODO` )

- Açıklama (metnin geri kalanı)

```csharp
// TODO: Load state from previously suspended application
```

Önceden `TODO` tanımlanmış bir belirteç olduğundan, bu açıklama listede görev olarak `TODO` görünür.

### <a name="custom-tokens"></a>Özel belirteçler

Varsayılan olarak, Visual Studio belirteçleri içerir: `HACK` , `TODO` , ve `UNDONE` `UnresolvedMergeConflict` . Bunlar büyük/küçük harfe duyarlı değildir. Ayrıca kendi özel belirteçlerinizi de oluşturabilirsiniz.

> [!NOTE]
> Varsayılan belirteçler yalnızca C/C++, C# ve VB dillerinde kullanılabilir. Diğer programlama dillerinde kendi belirteçlerinizi oluşturmak için aşağıdaki adımları kullanın.

Özel belirteç oluşturmak için:

1. Araçlar menüsünde **Seçenekler'i** **seçin.**

2. Ortam klasörünü **açın** ve ardından **Görev Listesi.**

   Görev Listesi [seçenekleri](../ide/reference/task-list-environment-options-dialog-box.md) sayfası görüntülenir.

   ![Visual Studio Görev Listesi](../ide/media/vs2015_task_list_options.png)

3. Ad **metin** kutusuna belirteç adını girin, örneğin **HATA.**

4. Öncelik **açılan** listesinde, yeni belirteç için varsayılan önceliği seçin.

5. **Ekle'yi seçin.**

> [!TIP]
> Ad **girdikten** sonra Ekle düğmesi etkinleştirilir. Ekle'ye tıklamadan önce bir ad girmeniz **gerekir.**

### <a name="c-todo-comments"></a>C++ TODO açıklamaları

Varsayılan olarak, C++ TODO yorumları **Görev Listesi.**

C++ TODO açıklamalarını kapatmak için  Araçlar menüsünde Seçenekler Metin Düzenleyici  >    >  **C/C++**  >    >   Açıklama Görevlerini Numaralandır'ı seçin ve değeri false olarak ayarlayın.

## <a name="shortcuts"></a>Kısayollar

*Kısayol,* koddaki yer işaretidir ve içinde **Görev Listesi.** Normal yer işaretinden farklı bir simgeye sahip. Kodda ilgili konuma **gitmek Görev Listesi** kısayola çift tıklayın.

![Visual Studio Görev Listesi Kısayol Simgesi](../ide/media/vs2015_task_list_bookmark.png)

### <a name="create-a-shortcut"></a>Kısayol oluşturma

Kısayol oluşturmak için, işaretçiyi koda bir kısayol eklemek istediğiniz yere girin. Yer   >  **İşaretlerini Düzenle**  >  **Kısayolu ekle'Görev Listesi veya** **Ctrl** + **K**, **Ctrl** + **H tuşlarına basın.**

Kodda kısayollar arasında gezinmek için, listeden bir kısayol  seçin ve ardından kısayol menüsünden Sonraki Görev **veya Önceki** Görev'i seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Listesi, Ortam, Seçenekler iletişim kutusu](../ide/reference/task-list-environment-options-dialog-box.md)
- [Görev yorumları (Mac için Visual Studio)](/visualstudio/mac/task-comments)
