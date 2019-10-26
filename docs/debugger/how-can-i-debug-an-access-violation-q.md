---
title: C++ Erişim ihlalinde hata ayıklama | Microsoft Docs
ms.custom: seodec18
ms.date: 02/05/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: f0235cc00a740069a77afd492cd585788ea666d2
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911470"
---
# <a name="how-can-i-debug-a-c-access-violation"></a>C++ Erişim ihlalinde nasıl hata ayıklayabilirim?

## <a name="problem-description"></a>Sorun açıklaması

Programımı bir erişim ihlali oluşturuyor. Bu, nasıl hata ayıklayabilirim?

## <a name="solution"></a>Çözüm

Birden çok işaretçiye giden bir kod satırı üzerinde erişim ihlali alırsanız, hangi işaretçinin erişim ihlaline neden olduğunu bulmak zor olabilir. Visual Studio 2015 güncelleştirme 1 ' den başlayarak, özel durum iletişim kutusu artık erişim ihlaline neden olan işaretçiyi açıkça adlandırır.

Örneğin, aşağıdaki kod verildiğinde bir erişim ihlali almanız gerekir:

```C++
#include <iostream>
using namespace std;

class ClassC {
public:
  void printHello() {
    cout << "hello world";
  }
};

class ClassB {
public:
  ClassC* C;
  ClassB() {
    C = new ClassC();
  }
};

class ClassA {
public:
  ClassB* B;
  ClassA() {
    // Uncomment to fix
    // B = new ClassB();
  }
};

int main() {
  ClassA* A = new ClassA();
  A->B->C->printHello();

}
```

Bu kodu Visual Studio 2015 güncelleştirme 1 ' de çalıştırırsanız, aşağıdaki özel durum iletişim kutusunu görmeniz gerekir:

![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")

İşaretçinin erişim ihlaline neden neden olduğunu belirleyemediğiniz takdirde, soruna neden olan işaretçinin doğru şekilde atandığından emin olmak için kodu izleyin.  Parametre olarak geçirildiyse, doğru şekilde geçirildiğinden ve yanlışlıkla [basit bir kopya](https://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy)oluşturmadığınızdan emin olun. Daha sonra, söz konusu işaretçinin programın başka bir yerinde değiştirilmediğinden emin olmak için söz konusu işaretçi için bir veri kesme noktası oluşturarak, bu değerlerin programda bir yerde yanlışlıkla değiştirilmediğini doğrulayın. Veri kesme noktaları hakkında daha fazla bilgi için [kesme noktaları kullanma](../debugger/using-breakpoints.md)içindeki veri kesme noktası bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kodda Hata Ayıklama SSS](../debugger/debugging-native-code-faqs.md)