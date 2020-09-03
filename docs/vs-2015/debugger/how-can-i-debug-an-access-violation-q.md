---
title: Erişim İhlalinde Nasıl Hata Ayıklayabilirim? | Microsoft Belgeleri
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f6188cc273cdea1755071e36f606fb8f041508d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297310"
---
# <a name="how-can-i-debug-an-access-violation"></a>Erişim İhlalinde Nasıl Hata Ayıklayabilirim?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sorun Açıklaması  
 Programımı bir erişim ihlali oluşturuyor. Bu, nasıl hata ayıklayabilirim?  
  
## <a name="solution"></a>Çözüm  
 Birden çok işaretçiye giden bir kod satırı üzerinde erişim ihlali alırsanız, hangi işaretçinin erişim ihlaline neden olduğunu bulmak zor olabilir. Visual Studio 2015 güncelleştirme 1 ' den başlayarak, özel durum iletişim kutusu artık erişim ihlaline neden olan işaretçiyi açıkça adlandırır.  
  
 Örneğin, aşağıdaki kod verildiğinde bir erişim ihlali almanız gerekir:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class ClassB {  
public:  
      ClassC* C;  
      ClassB() {  
            C = new ClassC();  
      }  
     void printHello() {  
            cout << "hello world";  
      }  
};  
  
class ClassA {  
public:  
    ClassB* B;  
    ClassA() {  
            B = nullptr;  
      }  
};  
  
int main() {  
    ClassA* A = new ClassA();  
    A->B->printHello();  
}  
```  
  
 Bu kodu Visual Studio 2015 güncelleştirme 1 ' de çalıştırırsanız, aşağıdaki özel durum iletişim kutusunu görmeniz gerekir:  
  
 ![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")  
  
 İşaretçinin erişim ihlaline neden neden olduğunu belirleyemediğiniz takdirde, soruna neden olan işaretçinin doğru şekilde atandığından emin olmak için kodu izleyin.  Parametre olarak geçirildiyse, doğru şekilde geçirildiğinden ve yanlışlıkla [basit bir kopya](https://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy)oluşturmadığınızdan emin olun. Daha sonra, söz konusu işaretçinin programın başka bir yerinde değiştirilmediğinden emin olmak için söz konusu işaretçi için bir veri kesme noktası oluşturarak, bu değerlerin programda bir yerde yanlışlıkla değiştirilmediğini doğrulayın. Veri kesme noktaları hakkında daha fazla bilgi için [kesme noktaları kullanma](../debugger/using-breakpoints.md)içindeki veri kesme noktası bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel Kod Hata Ayıklaması SSS](../debugger/debugging-native-code-faqs.md)
