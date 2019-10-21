---
title: Yeniden sıralama parametreleri yenidenC#düzenleme () | Microsoft Docs
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673141"
---
# <a name="reorder-parameters-refactoring-c"></a>Parametreleri Yeniden Sırala (C#) yeniden düzenlemesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters`, Yöntemler, C# Dizin oluşturucular ve temsilciler için parametrelerin sırasını değiştirmek için kolay bir yol sağlayan bir görsel yeniden düzenleme işlemidir. `Reorder Parameters` bildirimi değiştirir ve üyenin çağrıldığı tüm konumlarda parametreler yeni sırayı yansıtacak şekilde yeniden düzenlenir.

 @No__t_0 işlemini gerçekleştirmek için imleci bir yöntem, Dizin Oluşturucu veya temsilcinin üzerine veya yanına koyun. İmleç konumdayken, klavye kısayoluna basarak veya kısayol menüsünden komuta tıklayarak `Reorder Parameters` işlemini çağırın.

> [!NOTE]
> Bir genişletme yönteminde ilk parametreyi yeniden sırayükleyemezsiniz.

### <a name="to-reorder-parameters"></a>Parametreleri yeniden sıralamak için

1. @No__t_0 adlı bir sınıf kitaplığı oluşturun ve `Class1` aşağıdaki örnek kodla değiştirin.

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

2. İmleci yöntem bildiriminde ya da yöntem çağrısında `MethodB`.

3. Yeniden **Düzenle** menüsünde **parametreleri yeniden sırala**' ya tıklayın.

     **Parametreleri yeniden sırala** iletişim kutusu görüntülenir.

4. **Parametreleri yeniden sırala** iletişim kutusunda, **Parametreler** listesinden `int i` ' yi seçin ve ardından aşağı düğmesine tıklayın.

     Alternatif olarak, **Parametreler** listesinde `bool b` sonra `int i` sürükleyebilirsiniz.

5. **Parametreleri yeniden sırala** Iletişim kutusunda **Tamam**' a tıklayın.

     **Parametreleri yeniden sırala** iletişim kutusunda **başvuru değişikliklerini Önizle** seçeneği işaretliyse, **Değişiklikleri Önizle-parametreleri yeniden sırala** iletişim kutusu görüntülenir. İmza ve yöntem çağrısında `MethodB` için parametre listesindeki değişikliklerin önizlemesini sağlar.

    1. **Değişiklikleri Önizle-parametreleri yeniden sırala** iletişim kutusu görüntülenirse, **Uygula**' ya tıklayın.

         Bu örnekte, yöntem bildirimi ve `MethodB` için tüm yöntem çağrısı siteleri güncelleştirilir.

## <a name="remarks"></a>Açıklamalar
 Bir yöntem bildiriminden veya yöntem çağrısından parametreleri yeniden düzenleyebilirsiniz. İmleci Yöntem veya temsilci bildiriminin üzerine veya yanına konumlandırın, ancak gövdede değil.

## <a name="see-also"></a>Ayrıca Bkz.
 [Yeniden Düzenleme (C#)](../csharp-ide/refactoring-csharp.md)