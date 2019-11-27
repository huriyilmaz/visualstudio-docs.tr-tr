---
title: Erişim İhlalinde Nasıl Hata Ayıklayabilirim? | Microsoft Docs
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
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297310"
---
# <a name="how-can-i-debug-an-access-violation"></a>Erişim İhlalinde Nasıl Hata Ayıklayabilirim?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sorun açıklaması  
 Kendi programımı bir erişim ihlali üretir. Bu sorunu nasıl ayıklayabilirim?  
  
## <a name="solution"></a>Çözüm  
 Birden çok işaretçi başvuru kod satırında bir erişim ihlali alırsanız, hangi işaretçi erişim ihlaline neden olduğunu bulmak zor olabilir. Visual Studio 2015 güncelleştirme 1'de başlayarak, özel durum iletişim kutusunda artık açıkça erişim ihlaline neden işaretçi adları.  
  
 Örneğin, aşağıdaki kodu göz önünde bulundurulduğunda, bir erişim ihlali almanız gerekir:  
  
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
  
 Visual Studio 2015 güncelleştirme 1'de bu kodu çalıştırırsanız, aşağıdaki özel durum iletişim kutusunu görmeniz gerekir:  
  
 ![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")  
  
 İşaretçi erişim ihlaline neden neden belirleyemiyorsa, soruna işaretçi doğru şekilde atandığını emin olmak için kod boyunca izleme.  Parametre olarak geçirildiyse, doğru şekilde geçirildiğinden ve yanlışlıkla [basit bir kopya](https://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy)oluşturmadığınızdan emin olun. Daha sonra, söz konusu işaretçinin programın başka bir yerinde değiştirilmediğinden emin olmak için söz konusu işaretçi için bir veri kesme noktası oluşturarak, bu değerlerin programda bir yerde yanlışlıkla değiştirilmediğini doğrulayın. Veri kesme noktaları hakkında daha fazla bilgi için [kesme noktaları kullanma](../debugger/using-breakpoints.md)içindeki veri kesme noktası bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel Kodda Hata Ayıklama SSS](../debugger/debugging-native-code-faqs.md)
