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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594233"
---
# <a name="use-the-task-list"></a>Görev Listesini Kullanma

Belirteçler ve özel belirteçler `TODO` gibi `HACK`kod yorumlarını izlemek ve sizi doğrudan kodda önceden tanımlanmış bir konuma götürecek kısayolları yönetmek için **Görev Listesi'ni** kullanın. Kaynak kodundaki konumuna gitmek için listedeki öğeyi tıklatın.

> [!NOTE]
> Bu konu Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio için [Görev yorumlarına bakın (Mac için Visual Studio)](/visualstudio/mac/task-comments).

## <a name="the-task-list-window"></a>Görev Listesi penceresi

**Görev Listesi** açık olduğunda, uygulama penceresinin alt kısmında görünür.

Görev **Listesini**açmak için**Görev Listesini** **Görüntüle'yi** > seçin veya klavyeden **Ctrl**+**\\**,**T**tuşuna basın.

![Görev Listesi penceresi](../ide/media/vs2015_task_list.png)

Listenin sıralama sırasını değiştirmek için, herhangi bir sütunun üstbilgisini seçin. Arama sonuçlarınızı daha da hassaslaştırmak için **Shift** tuşuna basın ve ikinci bir sütun üstbilgisini tıklatın. Alternatif olarak, kısayol menüsünde **Sırayla'yı**seçin ve ardından bir üstbilgi seçin. Arama sonuçlarınızı daha da hassaslaştırmak için **Shift** tuşuna basın ve ikinci bir üstbilgi seçin.

Kısayol menüsünde sütunları göstermek veya gizlemek için **Sütunları Göster'i**seçin. Göstermek veya gizlemek istediğiniz sütunları seçin.

Sütunların sırasını değiştirmek için, herhangi bir sütun üstbilgisini istediğiniz konuma sürükleyin.

## <a name="user-tasks"></a>Kullanıcı görevleri

Visual Studio 2015'te kullanıcı görev özelliği kaldırıldı. Visual Studio 2013 ve önceki kullanıcı görev verilerine sahip bir çözüm *açtığınızda,.suo* dosyanızdaki kullanıcı görev verileri etkilenmez, ancak kullanıcı görevleri görev listesinde görüntülenmez.

Kullanıcı görev verilerinize erişmeye ve güncellemeye devam etmek istiyorsanız, Visual Studio 2013'te projeyi açın ve kullanıcı görevlerinin içeriğini tercih ettiğiniz proje yönetim aracına (Team Foundation Server gibi) kopyalayın.

## <a name="tokens-and-comments"></a>Belirteçler ve açıklamalar

Kodunuzda bir yorum işaretçisi ve önceden tanımlanmış bir belirteç öncesinde ki bir açıklama da **Görev Listesi'nde**görünür. Örneğin, aşağıdaki C# açıklamasının üç ayrı bölümü vardır:

- Yorum işaretçisi (`//`)

- Belirteç, örneğin`TODO`( )

- Açıklama (metnin geri kalanı)

```csharp
// TODO: Load state from previously suspended application
```

Önceden `TODO` tanımlanmış bir belirteç olduğundan, bu `TODO` açıklama listede bir görev olarak görünür.

> [!NOTE]
> Varsayılan belirteçler yalnızca C/C++, C#ve VB dilleri için kullanılabilir. Diğer diller için **Özel belirteçler** bölümüne bakın.

### <a name="custom-tokens"></a>Özel belirteçler

Varsayılan olarak, Visual Studio aşağıdaki belirteçleri `HACK`içerir: `TODO`, , `UNDONE`ve `UnresolvedMergeConflict`. Bunlar büyük/küçük harfe duyarlı değildir. Ayrıca kendi özel belirteçlerinizi de oluşturabilirsiniz.

Özel bir belirteç oluşturmak için:

1. **Araçlar** menüsünde **Seçenekler'i**seçin.

2. **Çevre** klasörünü açın ve ardından **Görev Listesi'ni**seçin.

   [Görev Listesi seçenekleri sayfası](../ide/reference/task-list-environment-options-dialog-box.md) görüntülenir.

   ![Visual Studio Görev Listesi](../ide/media/vs2015_task_list_options.png)

3. **Ad** metin kutusuna, örneğin **HATA**belirteç adınızı girin.

4. **Öncelik** açılır listesinde, yeni belirteç için varsayılan bir öncelik seçin.

5. **Ekle'yi**seçin.

> [!TIP]
> Bir ad girdikten sonra **Ekle** düğmesi etkin olur. **Ekle'yi**tıklatmadan önce bir ad girmeniz gerekir.

### <a name="c-todo-comments"></a>C++ TODO açıklamaları

Varsayılan olarak, C++ TODO yorumları **Görev Listesi'nde**görüntülenir.

**Araçlar** menüsünde C++ TODO yorumlarını kapatmak için **Seçenekler** > **Metin Düzenleyicisi** > **C/C++** > **Görünüm** > **Açıklama Görevlerini Sıralıyorum'u**seçin ve değeri **false**olarak ayarlayın.

## <a name="shortcuts"></a>Kısayollar

*Kısayol,* **Koddaki Görev Listesi'nde**izlenen yer imidir. Normal bir yer imi daha farklı bir simge vardır. Koddaki ilgili konuma gitmek için **Görev Listesi'ndeki** kısayolu çift tıklatın.

![Visual Studio Görev Listesi Kısayol Simgesi](../ide/media/vs2015_task_list_bookmark.png)

### <a name="create-a-shortcut"></a>Kısayol oluşturma

Kısayol oluşturmak için işaretçiyi kısayol yerleştirmek istediğiniz koda ekleyin. **Yer İşaretlerini** >  **Edit** > **Görev Listesi Kısayolu Ekle'yi** seçin veya Ctrl**K**, **Ctrl**+ **Ctrl**+**H**tuşuna basın.

Koddaki kısayollar arasında gezinmek için, listede bir kısayol seçin ve ardından kısayol menüsünden **Sonraki Görev** veya **Önceki Görev'i** seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Listesi, Çevre, Seçenekler iletişim kutusu](../ide/reference/task-list-environment-options-dialog-box.md)
- [Görev yorumları (Mac için Visual Studio)](/visualstudio/mac/task-comments)
