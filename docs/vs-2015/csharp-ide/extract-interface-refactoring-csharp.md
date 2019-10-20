---
title: Ayıklama arabirimi yeniden düzenlemesiC#() | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fdcf281e1ace40d1d7cdac0be302810ea173581b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667562"
---
# <a name="extract-interface-refactoring-c"></a>Ayıklama Arabirimi Yeniden Düzenlemesi (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ayıklama arabirimi, mevcut bir sınıf, yapı veya arabirimden kaynaklanan üyelere sahip yeni bir arabirim oluşturmanın kolay bir yolunu sağlayan bir yeniden düzenleme işlemidir.

 Birçok istemci, bir sınıf, yapı veya arabirimden aynı üye alt kümesini kullandıklarında veya birden çok sınıf, yapı veya arabirimlerin ortak bir üye alt kümesine sahip olduğu durumlarda, bir arabirimdeki üyelerin alt kümesini emkaya eklemek yararlı olabilir. Arabirimleri kullanma hakkında daha fazla bilgi için bkz. [arabirimler](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37).

 Ayıklama arabirimi yeni bir dosyada bir arabirim oluşturur ve imleci yeni dosyanın başlangıcında konumlandırır. Hangi üyelerin yeni arabirime ayıklanacağı, yeni arabirimin adının ve oluşturulan dosyanın adını, **arayüzü Ayıkla** iletişim kutusunu kullanarak belirtebilirsiniz.

### <a name="to-use-extract-interface"></a>Ayıklama arabirimini kullanmak için

1. @No__t_0 adlı bir konsol uygulaması oluşturun ve `Program` aşağıdaki kodla değiştirin

    ```csharp
    // Invoke Extract Interface on ProtoA.
    // Note:  the extracted interface will be created in a new file.
    class ProtoA
    {
        public void MethodB(string s) { }
    }
    ```

2. İmleci `MethodB` konumuna yerleştirilmiş ve yeniden **düzenleme** menüsünde **Arabirimi Ayıkla** ' ya tıklayın.

     **Arabirimi Ayıkla** iletişim kutusu görüntülenir.

     Ayrıca CTRL + R klavye kısayolunu yazarak, **arayüzü Ayıkla** iletişim kutusunu görüntüleyebilirsiniz.

     Ayrıca, fareyi sağ tıklayıp yeniden **Düzenle**' nin üzerine gelip **arabirimi** **Ayıkla iletişim kutusunu** görüntüleyebilirsiniz.

3. **Tümünü Seç**' e tıklayın.

4. **Tamam**'a tıklayın.

     Yeni dosya, IProtoA.cs ve aşağıdaki kodu görürsünüz:

    ```csharp
    using System;
    namespace TopThreeRefactorings
    {
        interface IProtoA
        {
            void MethodB(string s);
        }
    }
    ```

## <a name="remarks"></a>Açıklamalar
 Bu özellik yalnızca imleç, ayıklamak istediğiniz üyeleri içeren sınıf, yapı veya arayüzde konumlandırıldığında erişilebilir. İmleç bu konumdayken, arayüzü yeniden düzenleme işlemini çağırın.

 Bir sınıfta veya bir yapıda ayıklama arabirimini çağırdığınızda, tabanlar ve arabirimler listesi yeni arabirim adını içerecek şekilde değiştirilir. Bir arabirimde ayıklama arabirimini çağırdığınızda, tabanlar ve arabirimler listesi değiştirilmez.

## <a name="see-also"></a>Ayrıca Bkz.
 [Yeniden Düzenleme (C#)](../csharp-ide/refactoring-csharp.md)