---
title: C++ için Google Test nasıl kullanılır?
description: Visual Studio'da C++ birim testleri oluşturmak için Google Test'i kullanın.
ms.date: 05/06/2017
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 31078b060c94f3253232d22681a1a5dae47e03b6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77279299"
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Visual Studio'da C++ için Google Testi nasıl kullanılır?

Visual Studio 2017 ve sonraki alanlarda Google Test, C++ iş **yüküyle Masaüstü Geliştirme'nin** varsayılan bileşeni olarak Visual Studio IDE'ye entegre edilmiştir. Makinenize yüklü olduğunu doğrulamak için Visual Studio Yükleyici'yi açın ve google testini iş yükü bileşenleri listesinin altında bulun:

![Google Test'i Yükleyin](media/cpp-google-component.png)

::: moniker range="vs-2019"

## <a name="add-a-google-test-project-in-visual-studio-2019"></a>Visual Studio 2019'da Google Test projesi ekleme

1. **Çözüm Gezgini'nde,** çözüm düğümüne sağ tıklayın ve **Yeni Proje** **Ekle'yi** > seçin.
2. **Dil'i** **C++** olarak ayarlayın ve arama kutusuna **test** yazın. Sonuç listesinden **Google Test Project'i**seçin.
3. Test projesine bir ad verin ve **Tamam'ı**tıklatın.

![Yeni Google Test Projesi](media/vs-2019/cpp-gtest-new-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="add-a-google-test-project-in-visual-studio-2017"></a>Visual Studio 2017'de Google Test projesi ekleme

1. **Çözüm Gezgini'nde,** çözüm düğümüne sağ tıklayın ve **Yeni Proje** **Ekle'yi** > seçin.
2. Sol bölmede Visual **C++** > **Testi'ni** seçin ve ardından orta bölmede **Google Test Project'i** seçin.
3. Test projesine bir ad verin ve **Tamam'ı**tıklatın.

![Yeni Google Test Projesi](media/cpp-gtest-new-project.png)

::: moniker-end

## <a name="configure-the-test-project"></a>Test projesini yapılandırma

Görünen **Test Projesi Yapılandırması** iletişim kutusunda, sınamak istediğiniz projeyi seçebilirsiniz. Bir proje seçtiğinizde, Visual Studio seçilen projeye bir başvuru ekler. Proje seçmezseniz, test etmek istediğiniz projeye el ile başvuru eklemeniz gerekir. Google Test ikililerine statik ve dinamik bağlantı arasında seçim yaparken, göz önünde bulundurulması gereken hususlar herhangi bir C++ programı yla aynıdır. Daha fazla bilgi için [Visual C++ 'daki DL'lere](/cpp/build/dlls-in-visual-cpp)bakın.

![Google Test Projesini Yapılandırma](media/cpp-gtest-config.png)

## <a name="set-additional-options"></a>Ek seçenekler ayarlama

Ana menüden, ek seçenekler ayarlamak için Google Testi için **Araçlar** > **Seçenekleri** > **Test Bağdaştırıcısını** seçin. Bu ayarlar hakkında daha fazla bilgi için Google Test belgelerine bakın.

![Google Test Projesi ayarları](media/cpp-gtest-settings.png)

## <a name="add-include-directives"></a>Ekle yönergeleri

Test *.cpp* dosyanızda, programınızın türlerini ve işlevlerini test koduna görünür hale getirmek için gerekli `#include` yönergeleri ekleyin. Genellikle, program klasör hiyerarşisinde bir düzey yukarı. Bir IntelliSense penceresi yazarsanız `#include "../"` görünür ve üstbilgi dosyasına tam yolu seçmenize olanak tanır.

![#include yönergeleri ekleme](media/cpp-gtest-includes.png)

## <a name="write-and-run-tests"></a>Testleri yazma ve çalıştırma

Artık Google Testleri yazmaya ve çalıştırmaya hazırsınız. Test makroları hakkında bilgi için [Google Test astarına](https://github.com/google/googletest/blob/master/googletest/docs/primer.md) bakın. **Test**Gezgini'ni kullanarak testlerinizi keşfetme, çalıştırma ve gruplandırma hakkında bilgi için [Test Gezgini ile birim testleri](run-unit-tests-with-test-explorer.md) çalıştır'a bakın.

## <a name="see-also"></a>Ayrıca bkz.

[C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)
