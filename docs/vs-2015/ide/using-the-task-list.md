---
title: Görev Listesi kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
ms.assetid: f46a75a8-47b3-4cb6-bb59-b72e3356a664
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f7537c3007f54480874047f52f186996cf663508
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656402"
---
# <a name="using-the-task-list"></a>Görev Listesini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_1 ve `HACK` ya da özel belirteçler gibi belirteçleri kullanan kod açıklamalarını izlemek ve sizi doğrudan kodda önceden tanımlanmış bir konuma götüreceği kısayolları yönetmek için **görev listesi** kullanın. Kaynak kodundaki konumuna gitmek için listedeki öğeye tıklayın.

 Bu konuda:

- [Görev Listesi penceresi](../ide/using-the-task-list.md#taskListWindow)

- [Kullanıcı görevleri](../ide/using-the-task-list.md#userTasks)

- [Belirteçler ve açıklamalar](../ide/using-the-task-list.md#tokensComments)

- [Özel belirteçler](../ide/using-the-task-list.md#customTokens)

- [C++TODO açıklamaları](../ide/using-the-task-list.md#cppComments)

- [Kýsayol](../ide/using-the-task-list.md#shortcuts)

## <a name="taskListWindow"></a>Görev Listesi penceresi
 **Görev listesi** açık olduğunda, uygulama penceresinin alt kısmında görünür.

#### <a name="to-open-the-task-list"></a>Görev Listesi'ni açmak için

- **Görünüm** menüsünde **görev listesi** (klavye: CTRL + \\, t) öğesini seçin.

     ![Görev Listesi penceresi](../ide/media/vs2015-task-list.png "vs2015_task_list")

#### <a name="to-change-the-sort-order-of-the-list"></a>Listenin sıralama düzenini değiştirmek için

- Herhangi bir sütunun başlığına tıklayın. Arama sonuçlarınızı iyice daraltmak için Shift tuşuna basın ve ikinci bir sütun başlığına tıklayın.

     Alternatif olarak, kısayol menüsünde **Sırala**' yı seçin ve bir üst bilgi seçin. Arama sonuçlarınızı iyice daraltmak için Shift tuşuna basın ve ikinci bir başlık seçin.

#### <a name="to-show-or-hide-columns"></a>Sütunları göstermek veya gizlemek için

- Kısayol menüsünde **sütunları göster**' i seçin. Göstermek veya gizlemek istediğiniz sütunları seçin.

#### <a name="to-change-the-order-of-the-columns"></a>Sütunların sırasını değiştirmek için

- Herhangi bir sütun başlığını istediğiniz konuma sürükleyin.

## <a name="userTasks"></a>Kullanıcı görevleri
 Kullanıcı görevi özelliği Visual Studio 2015 ' de kaldırılmıştır. Visual Studio 2015 ' de Visual Studio 2013 ve önceki bir sürümden Kullanıcı görevi verileri içeren bir çözümü açtığınızda,. suo dosyanızdaki Kullanıcı görevi verileri etkilenmez, ancak Kullanıcı görevleri görev listesinde gösterilmez.

 Kullanıcı görev verilerinize erişmeye ve güncelleştirmeye devam etmek istiyorsanız, projeyi Visual Studio 2013 açmanız ve Kullanıcı görevlerinin içeriğini tercih ettiğiniz proje yönetim aracına (örneğin Team Foundation Server) kopyalamanız gerekir.

## <a name="tokensComments"></a>Belirteçler ve açıklamalar
 Kodunuzda bir açıklama işaretçisi ve önceden tanımlanmış bir belirteç, **görev listesi** penceresinde de görünür. Örneğin, aşağıdaki C# açıklamasının üç ayrı bölümü vardır:

- Açıklama işaretçisi (`//`)

- Belirteç, örneğin (`TODO`)

- Açıklama (metnin geri kalanı)

```
// TODO: Load state from previously suspended application
```

 @No__t_0 önceden tanımlanmış bir belirteç olduğundan, bu açıklama listede bir `TODO` görev olarak görünür.

### <a name="customTokens"></a>Özel belirteçler
 Varsayılan olarak, Visual Studio şu belirteçleri içerir: HACK, TODO, GERI ALıNDı, NOTE. Bunlar büyük/küçük harfe duyarlı değildir.

 Ayrıca kendi özel belirteçlerinizi de oluşturabilirsiniz.

##### <a name="to-create-a-custom-token"></a>Özel bir belirteç oluşturmak için

1. **Araçlar** menüsünde **Seçenekler**' i seçin.

2. **Ortam** klasörünü açın ve ardından **görev listesi**öğesini seçin.

     [Görev listesi, ortam, Seçenekler Iletişim kutusu](../ide/reference/task-list-environment-options-dialog-box.md) görüntülenir.

     ![Visual Studio Görev Listesi](../ide/media/vs2015-task-list-options.png "vs2015_task_list_options")

3. **Belirteçler** kategorisinde **ad** metin kutusuna belirteç adınızı gırın, örneğin "hata".

4. **Öncelik** açılan listesinde, yeni belirteç için varsayılan önceliği seçin. **Ekle** düğmesini seçin.

### <a name="cppComments"></a>C++ Todo açıklamaları
 Varsayılan olarak, C++ yapılacaklar açıklamaları **görev listesi** penceresinde görüntülenir. Bu davranışı değiştirebilirsiniz.

##### <a name="to-turn-off-c-todo-comments"></a>C++ Todo açıklamalarını kapatmak için

1. **Araçlar** menüsünde **Seçenekler &#124; metin Düzenleyicisi &#124; C/C++ &#124; görünüm açıklama görevlerini görüntüle &#124;**  ' ye gidin ve değeri false olarak ayarlayın.

2. **Seçenekler** Iletişim kutusunda **metin düzenleyici**' yi açın.

3. **CC++/** altında **Görünüm**' ü seçin ve açıklama oluşturma **görevlerini** **yanlış**olarak ayarlayın.

## <a name="shortcuts"></a>Kýsayol
 *Kısayol* , **görev listesi**izlenen koddaki bir yer işaretidir; Bu, düzenli bir yer işaretine göre farklı bir simgeye sahiptir. Koddaki ilgili konuma gitmek için **görev listesi** kısayoluna çift tıklayın.

 ![Visual Studio Görev Listesi kısayol simgesi](../ide/media/vs2015-task-list-bookmark.png "vs2015_task_list_bookmark")

#### <a name="to-create-a-shortcut"></a>Bir kısayol oluşturmak için

- İşaretçiyi, kod içinde kısayolu yerleştirmek istediğiniz yere ekleyin. **Yer Imlerini &#124; &#124; Düzenle Ekle görev listesi kısayolunu** seçin ya da (klavye: CTRL + K, CTRL + H) tuşuna basın.

     Koddaki kısayollar arasında gezinmek için listeden bir kısayol seçin ve sonra kısayol menüsünden **sonraki görev** veya **önceki görev** ' i seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Görev Listesi, Ortam, Seçenekler İletişim Kutusu](../ide/reference/task-list-environment-options-dialog-box.md)
