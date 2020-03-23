---
title: Derleme binası
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b5f00b3e71f0deb15d6266640db39751f2ae22f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76269098"
---
# <a name="compile-and-build-in-visual-studio"></a>Visual Studio'da derleme ve oluşturma

IDE içinde binaya ilk giriş [için, Bkz. Walkthrough: Bir uygulama oluşturma](walkthrough-building-an-application.md).

Bir uygulama oluşturmak için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz: Visual Studio IDE, MSBuild komut satırı araçları ve Azure Ardışık Hatları:

| Yapı Yöntemi | Avantajlar |
| --- |--- | --- |
| IDE |- Hemen oluşturur oluşturun ve bir hata ayıklama onları test edin.<br />- C++ ve C# projeleri için çok işlemcili yapılar çalıştırın.<br />- Yapı sisteminin farklı yönlerini özelleştirin. |
| CMake | - CMake aracını kullanarak projeler oluşturun<br />- Linux ve Windows platformlarında aynı yapı sistemini kullanın. |
| MSBuild komut satırı| - Visual Studio yüklemeden projeler oluşturun.<br />- Tüm proje türleri için çok işlemcili yapılar çalıştırın.<br />- Yapı sisteminin çoğu alanını özelleştirin.|
| Azure Pipelines | - Sürekli entegrasyon/sürekli teslimat boru hattının bir parçası olarak yapı sürecinizi otomatikleştirin.<br />- Her yapıya otomatik testler uygulayın.<br />- Yapı işlemleri için neredeyse sınırsız bulut tabanlı kaynak yararlanın.<br />- Yapı iş akışını değiştirin ve derinden özelleştirilmiş görevleri gerçekleştirmek için yapı etkinlikleri oluşturun.|

Bu bölümdeki belgeler, IDE tabanlı yapı sürecinin daha ayrıntılı olarak gider. Diğer yöntemler hakkında daha fazla bilgi için sırasıyla [MSBuild](../msbuild/msbuild.md) ve [Azure Ardışık Hatları'na](/azure/devops/pipelines/index?view=vsts)bakın.

> [!NOTE]
> Bu konu Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio için [Derleme'ye bakın ve Mac için Visual Studio'da oluşturun.](/visualstudio/mac/compiling-and-building)

## <a name="overview-of-building-from-the-ide"></a>IDE'den binaya genel bakış

Bir proje oluşturduğunuzda, Visual Studio proje ve projeyi içeren çözüm için varsayılan yapı yapılandırmaları oluşturdu.  Bu yapılandırmalar, çözümlerin ve projelerin nasıl oluşturulup dağıtılanları tanımlar. Özellikle proje yapılandırmaları bir hedef platform (Windows veya Linux gibi) ve yapı türü (hata ayıklama veya sürüm gibi) için benzersizdir. Bu yapılandırmaları istediğiniz gibi düzenleme yapabilir ve gerektiğinde kendi yapılandırmalarınızı da oluşturabilirsiniz.

IDE içinde binaya ilk giriş [için, Bkz. Walkthrough: Bir uygulama oluşturma](walkthrough-building-an-application.md).

Ardından, işleme yapabileceğiniz farklı yönlerini özelleştirmeler hakkında bilgi edinmek için [Visual Studio'da Bina ve temizlik projeleri ve çözümlerine](building-and-cleaning-projects-and-solutions-in-visual-studio.md) bakın. [Özelleştirmeler, çıktı dizinlerini değiştirmeyi,](how-to-change-the-build-output-directory.md) [özel yapı olaylarını belirtmeyi,](specifying-custom-build-events-in-visual-studio.md) [proje bağımlılıklarını yönetmeyi,](how-to-create-and-remove-project-dependencies.md)yapı günlüğü [dosyalarını yönetmeyi](how-to-view-save-and-configure-build-log-files.md)ve [derleyici uyarılarını bastırmayı](how-to-suppress-compiler-warnings.md)içerir.

Buradan, çeşitli görevleri keşfedebilirsiniz:
- [Derleme yapılandırmalarını anlama](understanding-build-configurations.md)
- [Derleme platformlarını anlama](understanding-build-platforms.md)
- [Proje ve çözüm özelliklerini yönetin.](managing-project-and-solution-properties.md)
- [C#](how-to-specify-build-events-csharp.md) ve Visual Basic'teki yapı olaylarını [belirtin.](how-to-specify-build-events-visual-basic.md)
- [Yapı seçeneklerini ayarlama](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Paralel olarak birden çok proje oluşturun.](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Web sitesi projeleri oluşturma (derleme)](https://msdn.microsoft.com/Library/a9cbb88c-8fff-4c67-848b-98fbfd823193)
- [Derlemeve oluşturma (Mac için Visual Studio)](/visualstudio/mac/compiling-and-building)
- [Visual Studio'da CMake projeleri](/cpp/build/cmake-projects-in-visual-studio)
