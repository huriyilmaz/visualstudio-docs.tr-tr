---
title: Görev Listesini Kullanma
description: Visual Studio Görev Listesi kod açıklamalarını daha verimli bir şekilde izlemenize ve kullanmanıza nasıl yardımcı olabileceğini öğrenin.
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
ms.openlocfilehash: f326885e0a98c4dc5a71f3024530d176951883101f126b0b2d9fe9755e843478
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121399489"
---
# <a name="use-the-task-list"></a>Görev Listesini Kullanma

Ve  , veya özel belirteçler gibi belirteçleri kullanan kod açıklamalarını izlemek `TODO` `HACK` ve sizi doğrudan kodda önceden tanımlanmış bir konuma götürür kısayolları yönetmek için görev listesi kullanın. Kaynak kodundaki konumuna gitmek için listedeki öğeye tıklayın.

> [!NOTE]
> bu konu Windows Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [görev açıklamaları (Mac için Visual Studio)](/visualstudio/mac/task-comments).

## <a name="the-task-list-window"></a>Görev Listesi penceresi

**Görev listesi** açık olduğunda, uygulama penceresinin alt kısmında görünür.

**Görev listesi** açmak için görev listesi **görüntüle**' yi seçin  >  veya klavyeden **CTRL** + **\\** ,**T** tuşlarına basın.

![Görev Listesi penceresi](../ide/media/vs2015_task_list.png)

Listenin sıralama düzenini değiştirmek için herhangi bir sütunun üst bilgisini seçin. Arama sonuçlarınızı daha da belirginleştirmek için **SHIFT** tuşuna basın ve ikinci bir sütun başlığına tıklayın. Alternatif olarak, kısayol menüsünde **sıralama ölçütü**' ni seçin ve ardından bir başlık seçin. Arama sonuçlarınızı daha da belirginleştirmek için **SHIFT** tuşuna basın ve ikinci bir başlık seçin.

Sütunları göstermek veya gizlemek için, kısayol menüsünde **sütunları göster**' i seçin. Göstermek veya gizlemek istediğiniz sütunları seçin.

Sütunların sırasını değiştirmek için herhangi bir sütun başlığını istediğiniz konuma sürükleyin.

## <a name="user-tasks"></a>Kullanıcı görevleri

kullanıcı görevi özelliği Visual Studio 2015 ' de kaldırıldı. Visual Studio 2013 ve önceki sürümlerinden kullanıcı görevi verileri içeren bir çözümü açtığınızda, *. suo* dosyanızdaki kullanıcı görevi verileri etkilenmez, ancak kullanıcı görevleri görev listesinde gösterilmez.

kullanıcı görev verilerinize erişmeye ve güncelleştirmeye devam etmek istiyorsanız, projeyi Visual Studio 2013 açın ve kullanıcı görevlerinin içeriğini tercih ettiğiniz proje yönetim aracına (Team Foundation Server gibi) kopyalayın.

## <a name="tokens-and-comments"></a>Belirteçler ve açıklamalar

Kodunuzda bir açıklama işaretçisi ve önceden tanımlanmış bir belirteç bulunan bir yorum de **görev listesi** görüntülenir. Örneğin, aşağıdaki C# açıklamasının üç ayrı bölümü vardır:

- Açıklama işaretçisi ( `//` )

- Belirteç, örneğin ( `TODO` )

- Açıklama (metnin geri kalanı)

```csharp
// TODO: Load state from previously suspended application
```

`TODO`, Önceden tanımlanmış bir belirteç olduğundan, bu açıklama listede bir `TODO` görev olarak görünür.

### <a name="custom-tokens"></a>Özel belirteçler

varsayılan olarak, Visual Studio aşağıdaki belirteçleri içerir: `HACK` , `TODO` , `UNDONE` ve `UnresolvedMergeConflict` . Bunlar büyük/küçük harfe duyarlı değildir. Ayrıca kendi özel belirteçlerinizi de oluşturabilirsiniz.

> [!NOTE]
> Varsayılan belirteçler yalnızca C/C++, C# ve VB dilleri için kullanılabilir. Diğer programlama dillerinde kendi belirteçlerinizi oluşturmak için aşağıdaki adımları kullanın.

Özel belirteç oluşturmak için:

1. **Araçlar** menüsünde **Seçenekler**' i seçin.

2. **Ortam** klasörünü açın ve ardından **görev listesi** öğesini seçin.

   [Görev listesi Seçenekler sayfası](../ide/reference/task-list-environment-options-dialog-box.md) görüntülenir.

   ![Visual Studio Görev Listesi](../ide/media/vs2015_task_list_options.png)

3. **Ad** metin kutusuna, belirteç adınızı girin, örneğin **hata**.

4. **Öncelik** açılan listesinde, yeni belirteç için varsayılan önceliği seçin.

5. **Ekle**' yi seçin.

> [!TIP]
> Ad girdikten sonra **Ekle** düğmesi etkin hale gelir. **Ekle**' ye tıklamadan önce bir ad girmeniz gerekir.

### <a name="c-todo-comments"></a>C++ TODO açıklamaları

Varsayılan olarak, C++ TODO açıklamaları **görev listesi** görüntülenir.

C++ Todo açıklamalarını kapatmak için, **Araçlar** menüsünde **Seçenekler**  >  **metin düzenleyici**  >  **C/C++**  >  **görünümü**  >  **Açıklama görevlerini numaralandır**' ı seçin ve değeri **false** olarak ayarlayın.

## <a name="shortcuts"></a>Kısayollar

*Kısayol* , **görev listesi** izlenen koddaki bir yer işaretidir. Bu, düzenli bir yer işaretine göre farklı bir simgeye sahiptir. Koddaki ilgili konuma gitmek için **görev listesi** kısayoluna çift tıklayın.

![Visual Studio Görev Listesi kısayol simgesi](../ide/media/vs2015_task_list_bookmark.png)

### <a name="create-a-shortcut"></a>Kısayol oluşturma

Bir kısayol oluşturmak için, işaretçiyi bir kısayol yerleştirmek istediğiniz koda ekleyin.   >  **Yer imlerini** Düzenle  >  **görev listesi kısayolunu** seçin veya **CTRL** + **K**, **CTRL** + **H** tuşlarına basın.

Koddaki kısayollar arasında gezinmek için listeden bir kısayol seçin ve sonra kısayol menüsünden **sonraki görev** veya **önceki görev** ' i seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Listesi, ortam, Seçenekler iletişim kutusu](../ide/reference/task-list-environment-options-dialog-box.md)
- [görev açıklamaları (Mac için Visual Studio)](/visualstudio/mac/task-comments)
