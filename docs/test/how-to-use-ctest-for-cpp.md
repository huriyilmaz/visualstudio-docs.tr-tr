---
title: C++ için CTest kullanma
description: Varsayılan olarak Visual Studio IDE ile tümleştirilmiş CTest ile test oluşturma ve çalıştırma hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 01/23/2020
ms.topic: how-to
ms.author: corob
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 845b20a18ccc422419084b8de0c9af725e105637
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033180"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio-2017-and-later"></a>Visual Studio 2017 ve sonrasında C++ için CTest kullanma

CMake (CTest içerir), **C++** ile Masaüstü Visual Studio'nin bir bileşeni olarak varsayılan olarak Visual Studio IDE ile tümleştirilmiştir. Makinenize yüklemeniz gerekirse, Visual Studio Yükleyicisi programını açın, **C++** ile Masaüstü Geliştirme düğmesine ve ardından Değiştir'e **tıklayın.** İş **yükü bileşenleri listesinin altında C++ Windows C++ CMake** araçlarını seçin.

## <a name="to-write-tests"></a>Testleri yazmak için

Visual Studio CMake desteği, proje sisteminin Visual Studio dahil değil. Bu nedenle, CTest testlerini her CMake ortamında olduğu gibi yazıp yapılandırabilirsiniz. Testi `enable_testing()` etkinleştirmek için komutunu ve yeni `add_test()` bir test eklemek için veya komutunu `gtest_discover_tests()` kullanın. CTest hakkında daha fazla bilgi edinmek için [CMake belgelerine bakın.](https://gitlab.kitware.com/cmake/community/wikis/doc/ctest/Testing-With-CTest) 

CMake'i uygulama içinde kullanma hakkında daha fazla Visual Studio için bkz. [Visual Studio.](/cpp/build/cmake-projects-in-visual-studio)

## <a name="to-run-tests"></a>Testleri çalıştırmak için

CTest, Test Gezgini ile tamamen **tümleşiktir ve** aynı zamanda hem Google hem de Boost birim testi çerçevelerini destekler. Bu çerçeveler varsayılan olarak C++ ile Masaüstü Geliştirme **iş yüküne bileşenler olarak** dahil edilir. Ancak, bir projeyi eski bir Visual Studio sürümünden yükseltıyorsanız, Visual Studio Yükleyicisi programını kullanarak bu çerçeveleri yüklemeniz gerekir.

Aşağıdaki çizimde, Google Test framework kullanılarak CTest çalıştırması sonuçları gösterilmiştir:

![Visual Studio'de Google Test Framework ile CTest](media/ctest-test-explorer.png)

CTest kullanıyorsanız ancak Google veya Boost bağdaştırıcılarını değil, sonuçları tek tek test yöntemi düzeyi yerine CTest düzeyinde görüntülersiniz. Yalnızca CTest yürütülebilir dosyalarında hata ayıklama ve adım adım yol kullanabilirsiniz, ancak tek tek testlerde yığın izlemeleri desteklenmiyor.

## <a name="see-also"></a>Ayrıca bkz.

- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)
