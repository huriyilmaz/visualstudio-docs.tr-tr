---
title: Parametreleri Kaldır yeniden düzenlemesiC#() | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.remove
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], removing
- refactoring [C#], Remove Parameters
- Remove Parameters refactoring [C#]
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40c373c3575f007952143e29c8dfc2cfac3d080f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667487"
---
# <a name="remove-parameters-refactoring-c"></a>Parametreleri Kaldır Yeniden Düzenlemesi (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Remove Parameters` Yöntemler, Dizin oluşturucular veya temsilcilerden parametreleri kaldırmanın kolay bir yolunu sağlayan bir yeniden düzenleme işlemidir. Parametreleri Kaldır bildirimi değiştirir; üyenin çağrıldığı herhangi bir konumda, parametresi yeni bildirimi yansıtacak şekilde kaldırılır.

 Önce imleci bir yöntem, Dizin Oluşturucu veya temsilci üzerinde konumlandırarak parametreleri Kaldır işlemini gerçekleştirirsiniz. İmleç konumdayken, kaldır `Parameters` işlemini çağırmak için yeniden **Düzenle** menüsüne tıklayın, klavye kısayoluna basın veya kısayol menüsünden komutu seçin.

> [!NOTE]
> Genişletme yöntemindeki ilk parametreyi kaldıramazsınız.

### <a name="to-remove-parameters"></a>Parametreleri kaldırmak için

1. @No__t_0 adlı bir konsol uygulaması oluşturun ve `Program` aşağıdaki kodla değiştirin.

    ```csharp
    class A
    {
        // Invoke on 'A'.
        public A(string s, int i) { }
    }

    class B
    {
        void C()
        {
            // Invoke on 'A'.
            A a = new A("a", 2);
        }
    }
    ```

2. İmleci yöntem bildiriminde ya da yöntem çağrısında `A` yöntemine yerleştirin.

3. Yeniden **Düzenle** **menüsünden parametreleri Kaldır iletişim kutusunu** göstermek için **parametreleri Kaldır** ' ı seçin.

     Ayrıca CTRL + R, V klavye kısayolunu yazarak **parametreleri Kaldır** iletişim kutusunu görüntüleyebilirsiniz.

     Ayrıca, imleci sağ tıklayıp yeniden **Düzenle**' nin üzerine gelin **ve parametreleri Kaldır iletişim kutusunu** göstermek için **parametreleri Kaldır** ' a tıklayabilirsiniz.

4. **Parametreler** alanını kullanarak imleci `int i` konuma konumlandırın ve sonra **Kaldır**' a tıklayın.

5. **Tamam**'a tıklayın.

6. **Önizleme değişiklikleri — parametreleri Kaldır** Iletişim kutusunda **Uygula**' ya tıklayın.

## <a name="remarks"></a>Açıklamalar
 Bir yöntem bildiriminden veya yöntem çağrısından parametreleri kaldırabilirsiniz. İmleci yöntem bildiriminde veya temsilci adıyla konumlandırın ve parametreleri Kaldır ' a çağırın.

> [!CAUTION]
> Parametreleri Kaldır, üyenin gövdesinde başvurulan bir parametreyi kaldırmanızı sağlar, ancak yöntem gövdesindeki bu parametreye başvuruları kaldırmaz. Bu, kodunuza derleme hataları getirebilir. Ancak, yeniden düzenleme işlemini yürütmeden önce kodunuzu gözden geçirmek için **Değişiklikleri Önizle** iletişim kutusunu kullanabilirsiniz.

 Bir yönteme yapılan çağrı sırasında kaldırılan bir parametre değiştirilirse, parametresinin kaldırılması değişikliği de kaldırır. Örneğin, bir yöntem çağrısı ' dan değiştirilirse

```csharp
MyMethod(param1++, param2);
```

 to

```csharp
MyMethod(param2);
```

 yeniden düzenleme işlemi tarafından `param1` artırılmayacak.

## <a name="see-also"></a>Ayrıca Bkz.
 [Yeniden Düzenleme (C#)](../csharp-ide/refactoring-csharp.md)