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
ms.openlocfilehash: 430d0e271f83332f7163c9c0c947f96756ca7a7d
ms.sourcegitcommit: e95dd8cedcd180e0bce6a75c86cf861757918290
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72165194"
---
# <a name="using-clang-tidy-in-visual-studio"></a>Visual Studio 'da Clang-Tidy kullanma

Kod Analizi, Clang veya MSVC Toolsets 'Ler kullanıp, hem MSBuild hem de CMake projeleri için [Clang-Tidy](https://clang.llvm.org/extra/clang-tidy/) 'ı yerel olarak destekler. Clang-Tidy denetimleri, arka plan kod analizinin bir parçası olarak çalışabilir, düzenleyici içi uyarılar (dalgalı çizgiler) olarak görünür ve Hata Listesi görüntüleyebilirsiniz.

Clang-Tidy kullanabilmeniz için, "C++ Windows için Clang araçları" bileşeni Visual Studio yükleyicisi aracılığıyla yüklenmelidir.

Clang-tidy, hem MSBuild hem de CMake 'te bulunan LLVM/Clang-CL araç takımını kullanırken varsayılan analiz aracıdır. MSVC araç takımını kullanırken, bunu birlikte çalışacak veya standart kod analizi deneyimini değiştirecek şekilde yapılandırabilirsiniz; Clang-CL araç takımını kullanıyorsanız Microsoft Kod Analizi kullanılamaz.

Clang-Tidy başarıyla derlemeden sonra çalışır; Clang-Tidy sonuçlarını almak için kaynak kodu hatalarını çözmeniz gerekebilir.


## <a name="msbuild"></a>MSBuild

Clang-Tidy ' i hem kod analizinin parçası olarak, hem de proje Özellikler penceresi **kod analizi** > **genel** sayfası altında çalışacak şekilde yapılandırabilirsiniz. Aracı yapılandırma seçenekleri, Clang-Tıdy alt menüsünde bulunabilir.

Daha fazla bilgi için [nasıl yapılır: C/C++ Projects @ no__t-1 Için kod analizi özelliklerini ayarlayın.

## <a name="cmake"></a>CMake

CMake projelerinde, `CMakeSettings.json` içinde Clang-Tidy denetimlerini yapılandırabilirsiniz. Açıldıktan sonra CMake proje ayarları Düzenleyicisi 'nin sağ üst köşesindeki "JSON 'u Düzenle" düğmesine tıklayın. Aşağıdaki anahtarlar tanınmalıdır:

- `enableMicrosoftCodeAnalysis`: Microsoft Kod analizini sunar
- `enableClangTidyCodeAnalysis`: Clang-Tidy analizini etkinleştirilir
- `clangTidyChecks`: Virgülle ayrılmış bir liste olarak belirtilen Clang-Tidy yapılandırması, etkin veya devre dışı bırakılacağını denetler

"Etkinleştir" seçeneklerinin hiçbiri belirtilmediyse, Visual Studio kullanılan platform araç takımı ile eşleşen analiz aracını seçer.

## <a name="warning-display"></a>Uyarı görüntüleme

Clang-tidy, Hata Listesi ve kodun ilgili bölümlerinin altında düzenleyici dalgalı çizgiler olarak görüntülenmiş uyarılarla sonuçlanır. Clang-Tıdy uyarılarını sıralamak ve düzenlemek için Hata Listesi "Category" sütununu kullanın. **Araçlar** > **seçenekleri**altındaki "Kod analizini devre dışı bırak" ayarını değiştirerek düzenleyici uyarılarını yapılandırabilirsiniz.

## <a name="clang-tidy-configuration"></a>Clang-Tidy yapılandırması

Clang-Tidy 'ın, **Clang-Tidy denetimleri** seçeneği aracılığıyla Visual Studio içinde çalıştığı denetimleri yapılandırabilirsiniz. Bu giriş, aracının **--denetimler** bağımsız değişkenine sağlanır. Daha fazla yapılandırma özel **. Clang-Tidy** dosyalarına dahil edilebilir. Daha fazla bilgi için [LLVM.org adresindeki Clang-Tidy belgelerine](https://clang.llvm.org/extra/clang-tidy/) bakın.

## <a name="see-also"></a>Ayrıca Bkz.

- [MSBuild projeleri için Clang/LLVM desteği](https://aka.ms/cpp/clangmsbuild)
- [CMake projeleri için Clang/LLVM desteği](https://aka.ms/cpp/clangcmake)
