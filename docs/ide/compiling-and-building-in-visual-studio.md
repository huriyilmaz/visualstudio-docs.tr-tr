---
title: Derleme derleniyor
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
ms.openlocfilehash: c55f229550dfe74606f4dfb0880b4e91d689d5ad
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809039"
---
# <a name="compile-and-build-in-visual-studio"></a>Visual Studio 'da derleme ve derleme

IDE içinde oluşturmaya ilk giriş için, bkz. [Izlenecek yol: uygulama oluşturma](walkthrough-building-an-application.md).

Bir uygulama oluşturmak için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz: Visual Studio IDE, MSBuild komut satırı araçları ve Azure Pipelines:

| Build yöntemi | Yararları |
| --- |--- | --- |
| IDE |-Derlemeleri hemen oluşturun ve bir hata ayıklayıcıda test edin.<br />-C++ ve C# projeleri için çok işlemcili derlemeler çalıştırın.<br />-Derleme sisteminin farklı yönlerini özelleştirin. |
| CMake | -CMake aracını kullanarak proje oluşturun<br />-Linux ve Windows platformları genelinde aynı derleme sistemini kullanın. |
| MSBuild komut satırı| -Visual Studio 'Yu yüklemeden projeler oluşturun.<br />-Tüm proje türleri için çok işlemcili derlemeler çalıştırın.<br />-Yapı sisteminin birçok alanını özelleştirin.|
| Azure Pipelines | -Derleme işleminizi sürekli tümleştirme/sürekli teslim işlem hattının parçası olarak otomatikleştirin.<br />-Her derleme ile otomatikleştirilmiş testler uygulayın.<br />-Derleme işlemlerinde neredeyse sınırsız sayıda bulut tabanlı kaynak kullanmayı.<br />-Derin özelleştirilmiş görevler gerçekleştirmek için derleme iş akışını değiştirin ve derleme etkinlikleri oluşturun.|

Bu bölümdeki belgeler, IDE tabanlı derleme sürecinin daha ayrıntılı ayrıntılarına gider. Diğer yöntemler hakkında daha fazla bilgi için sırasıyla [MSBuild](../msbuild/msbuild.md) ve [Azure Pipelines](/azure/devops/pipelines/index?view=vsts)bölümüne bakın.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için, bkz. [Mac için Visual Studio derleme ve derleme](/visualstudio/mac/compiling-and-building).

## <a name="overview-of-building-from-the-ide"></a>IDE 'den oluşturmaya genel bakış

Bir proje oluşturduğunuzda, Visual Studio proje için varsayılan derleme konfigürasyonları ve projeyi içeren çözüm için oluşturulmuştur.  Bu konfigürasyonlar, çözümlerin ve projelerin nasıl oluşturulup dağıtıldığını tanımlar. Özellikle de proje konfigürasyonları bir hedef platform (Windows veya Linux gibi) ve derleme türü (hata ayıklama veya sürüm gibi) için benzersizdir. Bu konfigürasyonları istediğiniz gibi düzenleyebilir ve gerektiğinde kendi yapılandırmalarınızı da oluşturabilirsiniz.

IDE içinde oluşturmaya ilk giriş için, bkz. [Izlenecek yol: uygulama oluşturma](walkthrough-building-an-application.md).

Ardından, işleme yapabileceğiniz farklı yönleri özelleştirmeleri hakkında bilgi edinmek için bkz. [Visual Studio 'da projeleri ve çözümleri oluşturma ve Temizleme](building-and-cleaning-projects-and-solutions-in-visual-studio.md) . Özelleştirmeler, [Çıkış dizinlerini değiştirme](how-to-change-the-build-output-directory.md), [özel derleme olayları belirtme](specifying-custom-build-events-in-visual-studio.md), [Proje bağımlılıklarını yönetme](how-to-create-and-remove-project-dependencies.md), [derleme günlüğü dosyalarını yönetme](how-to-view-save-and-configure-build-log-files.md)ve [derleyici uyarılarını gizleme](how-to-suppress-compiler-warnings.md)içerir.

Buradan, diğer birçok görevi inceleyebilirsiniz:
- [Derleme yapılandırmalarını anlama](understanding-build-configurations.md)
- [Derleme platformlarını anlama](understanding-build-platforms.md)
- [Proje ve çözüm özelliklerini yönetin](managing-project-and-solution-properties.md).
- [C#](how-to-specify-build-events-csharp.md) ve [Visual Basic](how-to-specify-build-events-visual-basic.md)derleme olaylarını belirtin.
- [Derleme seçeneklerini ayarla](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Paralel olarak birden çok proje oluşturun](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Web sitesi projelerini derleme (derleme)](/previous-versions/hwxa5aha(v=vs.140))
- [Derle ve derle (Mac için Visual Studio)](/visualstudio/mac/compiling-and-building)
- [Visual Studio 'da CMake projeleri](/cpp/build/cmake-projects-in-visual-studio)