---
title: C++ için CTest nasıl kullanılır?
ms.date: 01/23/2020
ms.topic: conceptual
ms.author: corob
manager: jillfra
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 78759a017575916bce3b3fff643cbce8ff303fd6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76826529"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio-2017-and-later"></a>Visual Studio 2017 ve sonrası c++ için CTest nasıl kullanılır?

CMake (CTest içerir) Varsayılan olarak C++ iş **yüküne sahip Masaüstü Geliştirme'nin** bir bileşeni olarak Visual Studio IDE'ye entegre edilir. Makinenize yüklemeniz gerekiyorsa, Visual Studio Installer programını açın, **C++** tuşu ile Masaüstü Geliştirme'yi tıklatın ve ardından **Değiştir'i**tıklatın. İş yükü bileşenleri listesinin altında **Windows için C++ CMake araçlarını** seçin.

## <a name="to-write-tests"></a>Testleri yazmak için

Visual Studio CMake desteği Visual Studio proje sistemi içermez. Bu nedenle, ctest testlerini herhangi bir CMake ortamında olduğu gibi yazar ve yapılandırırsınız. Testi `enable_testing()` etkinleştirmek için komutu, yeni bir test eklemek için `add_test()` veya komutu `gtest_discover_tests()` kullanın. CTest hakkında daha fazla bilgi edinmek için [CMake belgelerine](https://gitlab.kitware.com/cmake/community/wikis/doc/ctest/Testing-With-CTest)bakın. 

Visual Studio'da CMake kullanma hakkında daha fazla bilgi için [Visual Studio'daki CMake projelerine](/cpp/build/cmake-projects-in-visual-studio)bakın.

## <a name="to-run-tests"></a>Testleri çalıştırmak için

CTest, Test **Explorer** ile tam olarak entegre edilmiştir ve hem Google hem de Boost birim test çerçevelerini destekler. Bu çerçeveler varsayılan olarak C++ iş **yüküne sahip Masaüstü Geliştirme'de** bileşenler olarak dahil edilir. Ancak, Visual Studio'nun eski bir sürümünden bir projeyi yükseltiyorsanız, Visual Studio Installer programını kullanarak bu çerçeveleri yüklemeniz gerekebilir.

Aşağıdaki resimde, Google Test çerçevesi kullanılarak yapılan bir CTest çalışmasının sonuçları gösterilmektedir:

![Visual Studio'da Google Test Çerçevesi ile CTest](media/ctest-test-explorer.png)

CTest kullanıyorsanız ancak Google veya Boost bağdaştırıcıları kullanmıyorsanız, sonuçları tek tek test yöntemi düzeyi yerine CTest düzeyinde görürsünüz. Hata ayıklama ve yalnızca CTest tarafından çalıştırılabilir ler arasında adım atabilirsiniz, ancak tek tek testlerdeki yığın izleri desteklenmez.

## <a name="see-also"></a>Ayrıca bkz.

- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)
