---
title: Google Test için C++ kullanma
description: Visual Studio 'da birim C++ testleri oluşturmak için Google test kullanın.
ms.date: 05/06/2017
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 31078b060c94f3253232d22681a1a5dae47e03b6
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77279299"
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Visual Studio'da C++ için Google Test kullanma

Visual Studio 2017 ve üzeri sürümlerde Google test, Visual Studio IDE **ile birlikte C++**  iş yüküyle masaüstü geliştirmenin varsayılan bir bileşeni olarak tümleşiktir. Makinenizde yüklü olduğunu doğrulamak için Visual Studio Yükleyicisi'ni açın ve Google Test altında iş yükü bileşenlerin listesini bulun:

![Google Test yükle](media/cpp-google-component.png)

::: moniker range="vs-2019"

## <a name="add-a-google-test-project-in-visual-studio-2019"></a>Visual Studio 2019 ' de Google Test projesi ekleme

1. **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın ve > **Yeni proje** **Ekle** ' yi seçin.
2. Arama kutusuna dili **C++** olarak ayarlayın ve **Test** yazın. Sonuçlar listesinden **Google test proje**' yi seçin.
3. Test projesine bir ad verin ve **Tamam**' a tıklayın.

![Yeni Google Test projesi](media/vs-2019/cpp-gtest-new-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="add-a-google-test-project-in-visual-studio-2017"></a>Visual Studio 2017 ' de Google Test projesi ekleme

1. **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın ve > **Yeni proje** **Ekle** ' yi seçin.
2. Sol bölmede, **görsel C++**  > **Test** ' i seçin ve ardından orta bölmedeki **Google test proje** ' yi seçin.
3. Test projesine bir ad verin ve **Tamam**' a tıklayın.

![Yeni Google Test projesi](media/cpp-gtest-new-project.png)

::: moniker-end

## <a name="configure-the-test-project"></a>Test projesi yapılandırma

Görüntülenen **test projesi yapılandırması** iletişim kutusunda, test etmek istediğiniz projeyi seçebilirsiniz. Bir proje seçtiğinizde, Visual Studio Seçili projeye bir başvuru ekler. Hiçbir proje seçerseniz, test etmek istediğiniz projeleri başvuruları el ile eklemeniz gerekir. Statik ve dinamik Google Test ikili dosyalarına bağlanma arasında seçim yaparken, konuları herhangi bir C++ programı ile aynıdır. Daha fazla bilgi için bkz. [Visual C++içindeki dll 'ler ](/cpp/build/dlls-in-visual-cpp).

![Google Test projesi yapılandırma](media/cpp-gtest-config.png)

## <a name="set-additional-options"></a>Ek seçeneklerini ayarlama

Ek seçenekleri belirlemek için ana menüden **araçlar** > **Seçenekler** > **Google test için test bağdaştırıcısı** ' yı seçin. Bu ayarlar hakkında daha fazla bilgi için Google Test belgelerine bakın.

![Google Test projesi ayarları](media/cpp-gtest-settings.png)

## <a name="add-include-directives"></a>Ekleme yönergelerinde

Test *. cpp* dosyanızda, programınızın türlerini ve işlevlerini test koduna görünür hale getirmek için gerekli `#include` yönergelerini ekleyin. Genellikle, bir düzey klasör hiyerarşisindeki bir programdır. `#include "../"` yazarsanız bir IntelliSense penceresi görünür ve başlık dosyasının tam yolunu seçmenizi sağlar.

![Ekle #include](media/cpp-gtest-includes.png)

## <a name="write-and-run-tests"></a>Yazma ve testleri çalıştırma

Artık yazmak ve Google testleri çalıştırmak hazır olursunuz. Test makroları hakkında bilgi için [Google test](https://github.com/google/googletest/blob/master/googletest/docs/primer.md) bölümüne bakın. **Test Gezgini**'ni kullanarak testlerinizi bulma, çalıştırma ve gruplandırma hakkında bilgi için bkz. [Test Gezgini Ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md) .

## <a name="see-also"></a>Ayrıca bkz.

[C/için birim testleri yazmaC++](writing-unit-tests-for-c-cpp.md)
