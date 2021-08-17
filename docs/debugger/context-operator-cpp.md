---
title: Hata ayıklayıcısında bağlam işleci (C++) | Microsoft Docs
description: Dış kapsamda yer alan ve yerel bir adla gizlenen bir C++ adı için bağlam sağlamanız gerekir. Bunu yapmak için bağlam işleci kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.operators
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C++], native debugger
- evaluation
- format specifiers, expressions
- context operator, in expressions
- debugging [C++], expressions
- native expression evaluator
ms.assetid: 73cc9afe-f4a4-474e-bb89-5a33fb5e570c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: 6b59c4dfca1f56bdd08a2dc810524a698a869dc9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122031399"
---
# <a name="context-operator-in-the-visual-studio-debugger-c"></a>Visual Studio Debugger'da Bağlam İşleci (C++)
Bir kesme noktası konumunu, değişken adını veya ifadeyi nitelerken C++ bağlam işleci kullanabilirsiniz. Bağlam işleci, dış kapsamdan başka bir şekilde yerel adla gizlenen bir ad belirtmek için kullanışlıdır.

## <a name="syntax"></a><a name="BKMK_Using_context_operators_to_specify_a_symbol"></a> Sözdizimi
 Bağlamı belirtmenin iki yolu vardır:

1. {,,[*modül*] } *ifadesi*

     Küme ayraçları iki virgül ve modül (yürütülebilir veya DLL) adı veya tam yol içermesi gerekir.

     Örneğin, bir kesme noktası ayarlamak için `SomeFunction` EXAMPLE.dll:

    ```C++
    {,,EXAMPLE.dll}SomeFunction
    ```

2. *modülü*! *ifadesi*

    ```C++
    EXAMPLE.dll!SomeFunction
    ```

- *modül,* bir modülün adıdır. Aynı adla modüller arasında belirsizlikleri tam olarak ifade etmek için tam yol kullanabilirsiniz.

   Modül *yolunda* virgül, ekli alan veya ayraç varsa, bağlam ayrıştırıcının dizeyi düzgün şekilde tanıyaması için yolun etrafında tırnak işaretleri kullanmalıdır. Tek tırnak işaretleri, dosya adının Windows olarak kabul edilir, bu nedenle çift tırnak işareti kullanmalıdır. Örneğin,

  ```C++
  {,,"a long, long, library name.dll"} g_Var
  ```

- *ifadesi,* modülünde işlev adı, değişken adı veya işaretçi adresi gibi geçerli bir hedefe çözümleyici olan geçerli bir C++ *ifadesidir.*

  İfade değerlendiricisi bir ifadede bir sembolle karşılaştığında, sembolünü aşağıdaki sırayla arar:

1. Sözcük kapsamı dışa doğru, geçerli blokla başlayarak, küme ayraçları içine alınmış deyimler dizisi ve kapsayan blokla dışa doğru devam. Geçerli blok, geçerli konumu, yönerge işaretçisi adresini içeren koddur.

2. İşlev kapsamı. Geçerli işlev.

3. Geçerli konum bir C++ üye işlevinin içinde yer alıyorsa sınıf kapsamı. Sınıf kapsamı tüm temel sınıfları içerir. İfade değerlendiricisi normal hakimiyeti kurallarını kullanır.

4. Geçerli modülde genel semboller.

5. Geçerli programda ortak semboller.