---
title: Visual Studio 'da Clang-Tidy kullanma
ms.date: 10/04/2019
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
author: frozenpandaman
ms.author: efessler
ms.workload:
- cplusplus
ms.openlocfilehash: e226ac6c83839474b9d8ac6be7fb57e376de4a4f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745986"
---
# <a name="using-clang-tidy-in-visual-studio"></a>Visual Studio 'da Clang-Tidy kullanma

Kod Analizi, Clang veya MSVC Toolsets 'Ler kullanıp, hem MSBuild hem de CMake projeleri için [Clang-Tidy](https://clang.llvm.org/extra/clang-tidy/) 'ı yerel olarak destekler. Clang-Tidy denetimleri, arka plan kod analizinin bir parçası olarak çalışabilir, düzenleyici içi uyarılar (dalgalı çizgiler) olarak görünür ve Hata Listesi görüntüleyebilirsiniz.

Clang-Tidy kullanabilmeniz için, "C++ Windows için Clang araçları" bileşeni Visual Studio yükleyicisi aracılığıyla yüklenmelidir.

Clang-tidy, hem MSBuild hem de CMake 'te bulunan LLVM/Clang-CL araç takımını kullanırken varsayılan analiz aracıdır. MSVC araç takımını kullanırken, bunu birlikte çalışacak veya standart kod analizi deneyimini değiştirecek şekilde yapılandırabilirsiniz; Clang-CL araç takımını kullanıyorsanız Microsoft Kod Analizi kullanılamaz.

Clang-Tidy başarıyla derlemeden sonra çalışır; Clang-Tidy sonuçlarını almak için kaynak kodu hatalarını çözmeniz gerekebilir.


## <a name="msbuild"></a>MSBuild

Clang-Tidy ' i hem kod analizinin bir parçası olarak, hem de proje Özellikler penceresi **kod analizi**  > **genel** sayfası altında çalışacak şekilde yapılandırabilirsiniz. Aracı yapılandırma seçenekleri, Clang-Tıdy alt menüsünde bulunabilir.

Daha fazla bilgi için bkz. [nasıl yapılır: C/C++ projeleri Için kod analizi özelliklerini ayarlama](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="cmake"></a>CMake

CMake projelerinde, `CMakeSettings.json` içinde Clang-Tidy denetimlerini yapılandırabilirsiniz. Açıldıktan sonra CMake proje ayarları Düzenleyicisi 'nin sağ üst köşesindeki "JSON 'u Düzenle" düğmesine tıklayın. Aşağıdaki anahtarlar tanınmalıdır:

- `enableMicrosoftCodeAnalysis`: Microsoft Kod analizini etkinleştirilir
- `enableClangTidyCodeAnalysis`: Clang-Tıdy analizini etkinleştirilir
- `clangTidyChecks`: bir virgülle ayrılmış liste olarak belirtilen Clang-Tidy yapılandırması, etkin veya devre dışı bırakılacağını denetler

"Etkinleştir" seçeneklerinin hiçbiri belirtilmediyse, Visual Studio kullanılan platform araç takımı ile eşleşen analiz aracını seçer.

## <a name="warning-display"></a>Uyarı görüntüleme

Clang-tidy, Hata Listesi ve kodun ilgili bölümlerinin altında düzenleyici dalgalı çizgiler olarak görüntülenmiş uyarılarla sonuçlanır. Clang-Tıdy uyarılarını sıralamak ve düzenlemek için Hata Listesi "Category" sütununu kullanın. **Araçlar**  > **seçenekleri**altındaki "Kod analizini devre dışı bırak" ayarını değiştirerek düzenleyici uyarılarını yapılandırabilirsiniz.

## <a name="clang-tidy-configuration"></a>Clang-Tidy yapılandırması

Clang-Tidy 'ın, **Clang-Tidy denetimleri** seçeneği aracılığıyla Visual Studio içinde çalıştığı denetimleri yapılandırabilirsiniz. Bu giriş, aracının **--denetimler** bağımsız değişkenine sağlanır. Daha fazla yapılandırma özel **. Clang-Tidy** dosyalarına dahil edilebilir. Daha fazla bilgi için [LLVM.org adresindeki Clang-Tidy belgelerine](https://clang.llvm.org/extra/clang-tidy/) bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild projeleri için Clang/LLVM desteği](https://aka.ms/cpp/clangmsbuild)
- [CMake projeleri için Clang/LLVM desteği](https://aka.ms/cpp/clangcmake)
