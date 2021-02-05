---
title: C++ için Google Test kullanma
description: Visual Studio 'da C++ birim testleri oluşturmak için Google Test kullanın.
ms.date: 05/06/2017
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 6cf29d16432b677c6e83ba4cbaedb39f0a8d1ed2
ms.sourcegitcommit: 55bc9df751a21656de8cc5b6dbd8a2a1915ec690
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99572999"
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Visual Studio 'da C++ için Google Test kullanma

Visual Studio 2017 ve üzeri sürümlerde Google Test, Visual Studio IDE **Ile C++ iş yüküne sahip masaüstü geliştirmenin** varsayılan bir bileşeni olarak tümleşiktir. Makinenize yüklendiğini doğrulamak için Visual Studio Yükleyicisi açın ve iş yükü bileşenleri listesi altında Google Test bulun:

![Google Test yüklensin](media/cpp-google-component.png)

::: moniker range="vs-2019"

## <a name="add-a-google-test-project-in-visual-studio-2019"></a>Visual Studio 2019 ' de Google Test projesi ekleme

1. **Çözüm Gezgini**, çözüm düğümüne sağ tıklayıp  > **Yeni proje** Ekle ' yi seçin.
2. **Dili** **C++** olarak ayarlayın ve arama kutusuna **Test** yazın. Sonuçlar listesinden **Google test proje**' yi seçin.
3. Test projesine bir ad verin ve **Tamam**' a tıklayın.

![Yeni Google Test projesi](media/vs-2019/cpp-gtest-new-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="add-a-google-test-project-in-visual-studio-2017"></a>Visual Studio 2017 ' de Google Test projesi ekleme

1. **Çözüm Gezgini**, çözüm düğümüne sağ tıklayıp  > **Yeni proje** Ekle ' yi seçin.
2. Sol bölmede **Visual C++** > **Test** ' i seçin ve ardından orta bölmedeki **Google test proje** ' yi seçin.
3. Test projesine bir ad verin ve **Tamam**' a tıklayın.

![Yeni Google Test projesi](media/cpp-gtest-new-project.png)

::: moniker-end

## <a name="configure-the-test-project"></a>Test projesini yapılandırma

Görüntülenen **test projesi yapılandırması** iletişim kutusunda, test etmek istediğiniz projeyi seçebilirsiniz. Bir proje seçtiğinizde, Visual Studio Seçili projeye bir başvuru ekler. Proje yok ' u seçerseniz, test etmek istediğiniz proje (ler) e el ile başvuruları eklemeniz gerekir. Google Test ikilileri statik ve dinamik bağlama arasında seçim yaparken, tüm C++ programları ile aynıdır. Daha fazla bilgi için [Visual C++ Içindeki dll 'ler](/cpp/build/dlls-in-visual-cpp)bölümüne bakın.

![Google Test projesi yapılandırma](media/cpp-gtest-config.png)

## <a name="set-additional-options"></a>Ek seçenekleri ayarla

  >    >  Ek seçenekleri belirlemek için ana menüden Araçlar Seçenekler **Google test için test bağdaştırıcısı** seçin. Bu ayarlar hakkında daha fazla bilgi için Google Test belgelerine bakın.

![Google Test projesi ayarları](media/cpp-gtest-settings.png)

## <a name="add-include-directives"></a>İçerme yönergeleri ekleme

Test *. cpp* dosyanızda, `#include` programınızın türlerini ve işlevlerini test koduna görünür hale getirmek için gerekli yönergeleri ekleyin. Genellikle, program klasör hiyerarşisinde bir düzey yukarı açılır. `#include "../"`Bir IntelliSense penceresi yazdığınızda, başlık dosyasının tam yolunu seçmenizi sağlar.

![#İnclude yönergeleri ekleme](media/cpp-gtest-includes.png)

## <a name="write-and-run-tests"></a>Testleri yazma ve çalıştırma

Artık Google testlerini yazmaya ve çalıştırmaya hazırsınız. Test makroları hakkında bilgi için [Google test](https://github.com/google/googletest/blob/master/docs/primer.md) bölümüne bakın. **Test Gezgini**'ni kullanarak testlerinizi bulma, çalıştırma ve gruplandırma hakkında bilgi için bkz. [Test Gezgini Ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md) .

## <a name="see-also"></a>Ayrıca bkz.

[C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)
