---
title: Derleme
description: Visual Studio IDE derleme yöntemini, MSBuild komut satırı araçları derleme yöntemini veya Azure Pipelines derleme yöntemini kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 61abd28890fe92918c8ee2c9067820a781fac9c4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627237"
---
# <a name="compile-and-build-in-visual-studio"></a>Derleme ve derleme Visual Studio

IDE içinde binaya ilk giriş için bkz. [Adım adım kılavuz: Uygulama bina.](walkthrough-building-an-application.md)

Uygulama oluşturmak için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz: Visual Studio IDE, MSBuild komut satırı araçları ve Azure Pipelines:

| Derleme Yöntemi | Avantajlar |
| --- |--- | --- |
| IDE |- Derlemeleri hemen oluşturun ve bir hata ayıklayıcısında test edin.<br />- C++ ve C# projeleri için çok işlemcili derlemeler çalıştırın.<br />- Derleme sisteminin farklı yönlerini özelleştirin. |
| CMake | - CMake aracını kullanarak proje oluşturma<br />- Linux ve diğer platformlarda aynı derleme Windows kullanın. |
| MSBuild satırı| - Proje derlemelerini yüklemeden Visual Studio.<br />- Tüm proje türleri için çok işlemcili derlemeler çalıştırın.<br />- Derleme sisteminin çoğu alanlarını özelleştirin.|
| Azure Pipelines | - Sürekli tümleştirme/sürekli teslim işlem hattının bir parçası olarak derleme sürecinizi otomatikleştirin.<br />- Her derlemeyle otomatikleştirilmiş testler uygulama.<br />- Derleme işlemleri için neredeyse sınırsız bulut tabanlı kaynak kullanın.<br />- Derin özelleştirilmiş görevleri gerçekleştirmek için derleme iş akışını değiştirme ve derleme etkinlikleri oluşturma.|

Bu bölümdeki belgeler, IDE tabanlı derleme işleminin diğer ayrıntılarına gider. Diğer yöntemler hakkında daha fazla bilgi için [sırasıyla MSBuild](../msbuild/msbuild.md) [ve Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true)bakın.

> [!NOTE]
> Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio için [bkz. Derleme ve derleme Mac için Visual Studio.](/visualstudio/mac/compiling-and-building)

## <a name="overview-of-building-from-the-ide"></a>IDE'den binaya genel bakış

Bir proje oluşturulduğunda, Visual Studio ve projeyi içeren çözüm için varsayılan derleme yapılandırmaları oluşturulur.  Bu yapılandırmalar, çözümlerin ve projelerin nasıl yerleşik ve dağıtılmış olduğunu tanımlar. Project yapılandırmaları hedef platform (Windows veya Linux gibi) ve derleme türü (hata ayıklama veya yayın gibi) için benzersizdir. Bu yapılandırmaları istediğiniz gibi düzenleyebilir ve gerektiğinde kendi yapılandırmalarınızı da oluşturabilirsiniz.

IDE içinde binaya ilk giriş için bkz. [Adım adım kılavuz: Uygulama bina.](walkthrough-building-an-application.md)

Ardından, [süreçle ilgili olarak farklı özelleştirmeler hakkında Visual Studio](building-and-cleaning-projects-and-solutions-in-visual-studio.md) için bkz. Proje ve çözümler derleme ve temizleme. Özelleştirmeler, [çıkış dizinlerini](how-to-change-the-build-output-directory.md) [değiştirmeyi,](specifying-custom-build-events-in-visual-studio.md)özel derleme olaylarını [belirtmeyi,](how-to-create-and-remove-project-dependencies.md)proje bağımlılıklarını yönetmeyi, [](how-to-view-save-and-configure-build-log-files.md)derleme günlük dosyalarını yönetmeyi ve derleyici [uyarılarını gizlemeyi içerir.](how-to-suppress-compiler-warnings.md)

Buradan, diğer çeşitli görevleri keşfedebilirsiniz:
- [Derleme yapılandırmalarını anlama](understanding-build-configurations.md)
- [Derleme platformlarını anlama](understanding-build-platforms.md)
- [Proje ve çözüm özelliklerini yönetme.](managing-project-and-solution-properties.md)
- C# içinde derleme [olaylarını belirtin ve](how-to-specify-build-events-csharp.md) [Visual Basic.](how-to-specify-build-events-visual-basic.md)
- [Derleme seçeneklerini ayarlama](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Birden çok proje paralel olarak derleme.](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Web sitesi projeleri derleme (derleme)](/previous-versions/hwxa5aha(v=vs.140))
- [Derleme ve derleme (Mac için Visual Studio)](/visualstudio/mac/compiling-and-building)
- [Visual Studio'de CMake projeleri](/cpp/build/cmake-projects-in-visual-studio)