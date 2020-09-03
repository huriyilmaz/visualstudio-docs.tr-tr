---
title: Parametreleri yeniden düzenleme yeniden düzenlemesi (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e39564fb108b63859620e2c4a650608cdf1e7e82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673141"
---
# <a name="reorder-parameters-refactoring-c"></a>Parametreleri Yeniden Sırala (C#) yeniden düzenlemesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters` Yöntemler, Dizin oluşturucular ve temsilciler için parametrelerin sırasını değiştirmek için kolay bir yol sağlayan bir Visual C# yeniden düzenleme işlemidir. `Reorder Parameters` bildirimi değiştirir ve üyenin çağrıldığı tüm konumlarda parametreler yeni sırayı yansıtacak şekilde yeniden düzenlenir.

 İşlemi gerçekleştirmek için `Reorder Parameters` , imleci bir yöntem, Dizin Oluşturucu veya temsilcinin üzerine veya yanına koyun. İmleç konumdayken, `Reorder Parameters` klavye kısayoluna basarak veya kısayol menüsünden komuta tıklayarak işlemi çağırın.

> [!NOTE]
> Bir genişletme yönteminde ilk parametreyi yeniden sırayükleyemezsiniz.

### <a name="to-reorder-parameters"></a>Parametreleri yeniden sıralamak için

1. Adlı bir sınıf kitaplığı oluşturun `ReorderParameters` ve ardından `Class1` Aşağıdaki örnek kodla değiştirin.

    ```csharp
    class ProtoClassA
    {
        // Invoke on 'MethodB'.
        public void MethodB(int i, bool b) { }
    }

    class ProtoClassC
    {
        void D()
        {
            ProtoClassA MyClassA = new ProtoClassA();

            // Invoke on 'MethodB'.
            MyClassA.MethodB(0, false);
        }
    }
    ```

2. İmleci `MethodB` , yöntem bildiriminde ya da yöntem çağrısında yerleştirin.

3. Yeniden **Düzenle** menüsünde **parametreleri yeniden sırala**' ya tıklayın.

     **Parametreleri yeniden sırala** iletişim kutusu görüntülenir.

4. **Parametreleri yeniden sırala** Iletişim kutusunda `int i` **Parametreler** listesinden öğesini seçin ve ardından aşağı düğmesine tıklayın.

     Alternatif olarak, `int i` `bool b` **Parametreler** listesinden sonra sürükleyebilirsiniz.

5. **Parametreleri yeniden sırala** Iletişim kutusunda **Tamam**' a tıklayın.

     **Parametreleri yeniden sırala** iletişim kutusunda **başvuru değişikliklerini Önizle** seçeneği işaretliyse, **Değişiklikleri Önizle-parametreleri yeniden sırala** iletişim kutusu görüntülenir. İmza ve yöntem çağrısında, parametre listesindeki değişikliklerin önizlemesini sağlar `MethodB` .

    1. **Değişiklikleri Önizle-parametreleri yeniden sırala** iletişim kutusu görüntülenirse, **Uygula**' ya tıklayın.

         Bu örnekte, için yöntem bildirimi ve tüm yöntem çağrısı siteleri `MethodB` güncelleştirilir.

## <a name="remarks"></a>Açıklamalar
 Bir yöntem bildiriminden veya yöntem çağrısından parametreleri yeniden düzenleyebilirsiniz. İmleci Yöntem veya temsilci bildiriminin üzerine veya yanına konumlandırın, ancak gövdede değil.

## <a name="see-also"></a>Ayrıca Bkz.
 [Yeniden Düzenleme (C#)](../csharp-ide/refactoring-csharp.md)