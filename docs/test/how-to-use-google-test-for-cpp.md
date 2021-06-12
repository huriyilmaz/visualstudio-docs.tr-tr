---
title: C++ için Google Test kullanma
description: Google Test C++ birim testleri oluşturmak için Visual Studio.
ms.date: 05/06/2017
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: a338b6f62aee6ec342ef6a16abec71cb6a833bc0
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042970"
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Visual Studio'da C++ için Google Test'yi kullanma

2017 Visual Studio ve sonraki bir Google Test, **C++** ile Masaüstü Geliştirme iş yükünün varsayılan bileşeni olarak Visual Studio IDE ile tümleştirilmiştir. Makinenize yüklü olduğunu doğrulamak için, Visual Studio Yükleyicisi açın ve Google Test bileşenleri listesinden aşağıdaki bilgileri bulun:

![Yükleme Google Test](media/cpp-google-component.png)

::: moniker range=">=vs-2019"

## <a name="add-a-google-test-project-in-visual-studio-2019"></a>Visual Studio 2019'da Google Test projesi ekleme

1. Bu **Çözüm Gezgini,** çözüm düğümüne sağ tıklayın ve Yeni Proje **Ekle'yi** > **seçin.**
2. **Dil'i** **C++ olarak** ayarlayın ve arama kutusuna **test** yazın. Sonuçlar listesinden Proje'yi **Google Test seçin.**
3. Test projesine bir ad girin ve Tamam'a **tıklayın.**

![Yeni Google Test Projesi](media/vs-2019/cpp-gtest-new-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="add-a-google-test-project-in-visual-studio-2017"></a>Visual Studio 2017'de Google Test projesi ekleme

1. Bu **Çözüm Gezgini,** çözüm düğümüne sağ tıklayın ve Yeni Proje **Ekle'yi** > **seçin.**
2. Sol bölmede **Test'Visual C++** > **seçin** ve ardından orta **bölmede Google Test Project'i** seçin.
3. Test projesine bir ad girin ve Tamam'a **tıklayın.**

![Yeni Google Test Projesi](media/cpp-gtest-new-project.png)

::: moniker-end

## <a name="configure-the-test-project"></a>Test projesini yapılandırma

Görüntülenen **Test Projesi Yapılandırması** iletişim kutusunda test etmek istediğiniz projeyi seçebilirsiniz. Bir proje seçerseniz, Visual Studio projeye bir başvuru ekler. Proje seçmezsiniz, test etmek istediğiniz proje veya projelere başvuruları el ile eklemeniz gerekir. Statik ve dinamik bağlama arasında seçim Google Test, dikkat edilmesi gerekenler tüm C++ programlarına göre aynıdır. Daha fazla bilgi için bkz. [Visual C++.](/cpp/build/dlls-in-visual-cpp)

![Google Test Projesini Yapılandırma](media/cpp-gtest-config.png)

## <a name="set-additional-options"></a>Ek seçenekleri ayarlama

Ana menüden Araçlar **Seçenekler'i**  >  **seçin**  >  **Google Test için Test Bağdaştırıcısı** seçenekleri ayarlayın. Bu ayarlar Google Test daha fazla bilgi için aşağıdaki belgeye bakın.

![Google Test Proje ayarları](media/cpp-gtest-settings.png)

## <a name="add-include-directives"></a>Ekleme yönergeleri ekleme

Test *.cpp dosyanıza,* program tür ve işlevlerini test koduna görünür hale eklemek için `#include` gerekli yönergeleri ekleyin. Genellikle, program klasör hiyerarşisinde bir düzey yukarıdır. Bir `#include "../"` IntelliSense penceresi açarsanız, üst bilgi dosyasının tam yolunu seçmenize olanak sağlar.

![#include yönergeleri ekleme](media/cpp-gtest-includes.png)

## <a name="write-and-run-tests"></a>Testleri yazma ve çalıştırma

Artık Google Testlerini yazmaya ve çalıştırmaya hazır olursanız. Test [makroları Google Test](https://github.com/google/googletest/blob/master/docs/primer.md) bilgi için aşağıdaki genel bilgilere bakın. Test [Gezgini'ni kullanarak testlerinizi bulma,](run-unit-tests-with-test-explorer.md) çalıştırma ve gruplama hakkında bilgi için bkz. Test Gezgini ile **birim testleri çalıştırma.**

## <a name="see-also"></a>Ayrıca bkz.

[C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)
