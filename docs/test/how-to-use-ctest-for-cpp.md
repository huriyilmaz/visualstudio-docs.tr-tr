---
title: C++ için CTest kullanma
ms.date: 01/23/2020
ms.topic: conceptual
ms.author: corob
manager: jillfra
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 78759a017575916bce3b3fff643cbce8ff303fd6
ms.sourcegitcommit: 8cbced0fb46959a3a2494852df1e41db1177a26c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76826529"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio-2017-and-later"></a>Visual Studio 2017 ve üzeri sürümlerde C++ ctest kullanımı

CMake (ctest içeren), varsayılan olarak iş yüküyle **masaüstü geliştirme C++**  bileşeni olarak Visual Studio IDE ile tümleşiktir. Makinenize yüklemeniz gerekiyorsa Visual Studio yükleyicisi programını açın, **ile C++ masaüstü geliştirme** düğmesine tıklayın ve ardından **Değiştir**' e tıklayın. İş yükü bileşenleri listesi altında  **C++ Windows için CMake Araçları ' nı** seçin.

## <a name="to-write-tests"></a>Testler yazmak için

Visual Studio'da CMake desteği, Visual Studio Proje sistemi kullanılmaz. Bu nedenle, yazma ve herhangi bir CMake ortamında olduğu gibi CTest testler yapılandırın. Testi etkinleştirmek için `enable_testing()` komutunu ve yeni bir test eklemek için `add_test()` veya `gtest_discover_tests()` komutunu kullanın. CTest hakkında daha fazla bilgi için bkz. [CMake belgeleri](https://gitlab.kitware.com/cmake/community/wikis/doc/ctest/Testing-With-CTest). 

Visual Studio 'da CMake 'i kullanma hakkında daha fazla bilgi için bkz. [Visual Studio 'Da CMake projeleri](/cpp/build/cmake-projects-in-visual-studio).

## <a name="to-run-tests"></a>Testleri çalıştırmak için

CTest, **Test Gezgini** ile tamamen tümleşiktir ve hem Google hem de Boost birim testi çerçevelerini destekler. Bu çerçeveler, varsayılan olarak, iş yüküyle **Masaüstü geliştirmenin C++**  bileşenleri olarak eklenir. Ancak, bir projeyi Visual Studio'nun eski bir sürümden yükseltiyorsanız, Visual Studio yükleyicisi programını kullanarak bu çerçeveleri yüklemeniz gerekebilir.

Aşağıdaki çizim bir CTest, Google Test çerçevesini kullanarak çalıştırma sonuçları gösterilmektedir:

![Visual Studio 'da Google Test Framework ile CTest](media/ctest-test-explorer.png)

CTest ancak değil Google veya Boost bağdaştırıcıları kullanıyorsanız, yöntem düzeyine test sonuçları yerine tek tek CTest düzeyinde bakın. Hata ayıklaması yapabilirsiniz ve adım adım yalnızca CTest yürütülebilir dosyaları, ancak yığın izlemelerini bireysel testler üzerinde desteklenmez.

## <a name="see-also"></a>Ayrıca bkz.

- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)
