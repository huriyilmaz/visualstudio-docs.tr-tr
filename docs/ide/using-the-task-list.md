---
title: Görev Listesini Kullanma
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db39850350f99e6c046996f6408973cbc6543868
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594233"
---
# <a name="use-the-task-list"></a>Görev Listesini Kullanma

`TODO` ve `HACK`ya da özel belirteçler gibi belirteçleri kullanan kod açıklamalarını izlemek ve sizi doğrudan kodda önceden tanımlanmış bir konuma götürür kısayolları yönetmek için **görev listesi** kullanın. Kaynak kodundaki konumuna gitmek için listedeki öğeye tıklayın.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [görev açıklamaları (Mac için Visual Studio)](/visualstudio/mac/task-comments).

## <a name="the-task-list-window"></a>Görev Listesi penceresi

**Görev listesi** açık olduğunda, uygulama penceresinin alt kısmında görünür.

**Görev listesi**açmak Için, **Görünüm** > **görev listesi**' yı seçin veya klavyede **CTRL**+ **\\** ,**t**tuşlarına basın.

![Görev Listesi penceresi](../ide/media/vs2015_task_list.png)

Listenin sıralama düzenini değiştirmek için herhangi bir sütunun üst bilgisini seçin. Arama sonuçlarınızı daha da belirginleştirmek için **SHIFT** tuşuna basın ve ikinci bir sütun başlığına tıklayın. Alternatif olarak, kısayol menüsünde **sıralama ölçütü**' ni seçin ve ardından bir başlık seçin. Arama sonuçlarınızı daha da belirginleştirmek için **SHIFT** tuşuna basın ve ikinci bir başlık seçin.

Sütunları göstermek veya gizlemek için, kısayol menüsünde **sütunları göster**' i seçin. Göstermek veya gizlemek istediğiniz sütunları seçin.

Sütunların sırasını değiştirmek için herhangi bir sütun başlığını istediğiniz konuma sürükleyin.

## <a name="user-tasks"></a>Kullanıcı görevleri

Kullanıcı görevi özelliği Visual Studio 2015 ' de kaldırılmıştır. Visual Studio 2013 ve önceki sürümlerinden Kullanıcı görevi verileri içeren bir çözümü açtığınızda, *. suo* dosyanızdaki Kullanıcı görevi verileri etkilenmez, ancak Kullanıcı görevleri görev listesinde gösterilmez.

Kullanıcı görev verilerinize erişmeye ve güncelleştirmeye devam etmek istiyorsanız, projeyi Visual Studio 2013 açın ve Kullanıcı görevlerinin içeriğini tercih ettiğiniz proje yönetim aracına (Team Foundation Server gibi) kopyalayın.

## <a name="tokens-and-comments"></a>Belirteçler ve açıklamalar

Kodunuzda bir açıklama işaretçisi ve önceden tanımlanmış bir belirteç bulunan bir yorum de **görev listesi**görüntülenir. Örneğin, aşağıdaki C# açıklamasının üç ayrı bölümü vardır:

- Açıklama işaretçisi (`//`)

- Belirteç, örneğin (`TODO`)

- Açıklama (metnin geri kalanı)

```csharp
// TODO: Load state from previously suspended application
```

`TODO` önceden tanımlanmış bir belirteç olduğundan, bu açıklama listede bir `TODO` görev olarak görünür.

> [!NOTE]
> Varsayılan belirteçler yalnızca C/C++, C#, ve vb dilleri için kullanılabilir. Diğer diller için bkz. **özel belirteçler** bölümü.

### <a name="custom-tokens"></a>{1&gt;Özel belirteçler&lt;1}

Varsayılan olarak, Visual Studio aşağıdaki belirteçleri içerir: `HACK`, `TODO`, `UNDONE`ve `UnresolvedMergeConflict`. Bunlar büyük/küçük harfe duyarlı değildir. Ayrıca kendi özel belirteçlerinizi de oluşturabilirsiniz.

Özel belirteç oluşturmak için:

1. Üzerinde **Araçları** menüsünde seçin **seçenekleri**.

2. **Ortam** klasörünü açın ve ardından **görev listesi**öğesini seçin.

   [Görev listesi Seçenekler sayfası](../ide/reference/task-list-environment-options-dialog-box.md) görüntülenir.

   ![Visual Studio Görev Listesi](../ide/media/vs2015_task_list_options.png)

3. **Ad** metin kutusuna, belirteç adınızı girin, örneğin **hata**.

4. **Öncelik** açılan listesinde, yeni belirteç için varsayılan önceliği seçin.

5. Seçin **ekleme**.

> [!TIP]
> Ad girdikten sonra **Ekle** düğmesi etkin hale gelir. **Ekle**' ye tıklamadan önce bir ad girmeniz gerekir.

### <a name="c-todo-comments"></a>C++ TODO açıklamaları

Varsayılan olarak, C++ yapılacaklar açıklamaları **görev listesi**görüntülenir.

C++ Todo açıklamalarını kapatmak için, **Araçlar** menüsünde **Seçenekler** > **metin düzenleyici** > **C/C++**  >  > **Açıklama görevlerini** **görüntüle** ' yi seçin ve değeri **false**olarak ayarlayın.

## <a name="shortcuts"></a>Kısayollar

*Kısayol* , **görev listesi**izlenen koddaki bir yer işaretidir. Bu, düzenli bir yer işaretine göre farklı bir simgeye sahiptir. Koddaki ilgili konuma gitmek için **görev listesi** kısayoluna çift tıklayın.

![Visual Studio Görev Listesi kısayol simgesi](../ide/media/vs2015_task_list_bookmark.png)

### <a name="create-a-shortcut"></a>Kısayol oluşturma

Bir kısayol oluşturmak için, işaretçiyi bir kısayol yerleştirmek istediğiniz koda ekleyin.  > **yer Imlerini** **Düzenle** > **görev listesi kısayol Ekle** ' yi seçin veya **CTRL**+**K**, **CTRL**+**H**tuşlarına basın.

Koddaki kısayollar arasında gezinmek için listeden bir kısayol seçin ve sonra kısayol menüsünden **sonraki görev** veya **önceki görev** ' i seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Listesi, ortam, Seçenekler iletişim kutusu](../ide/reference/task-list-environment-options-dialog-box.md)
- [Görev açıklamaları (Mac için Visual Studio)](/visualstudio/mac/task-comments)
