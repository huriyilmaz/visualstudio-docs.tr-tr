---
title: Derleme ve Oluşturma
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d8ec7d6508ec025a2b2005754da03bdd4db38943
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300269"
---
# <a name="compiling-and-building-in-visual-studio"></a>Visual Studio'da Derleme ve Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'Yu kullanarak uygulamalar oluşturabilir ve bir geliştirme sürecinde sık sık aralıklarla derlemeler ve yürütülebilir programlar oluşturabilirsiniz. Kodunuzun sıklıkla derlenmesi için yanlış sözdizimi, yanlış yazılmış anahtar sözcükler ve tür uyuşmazlıkları gibi derleme zamanı hatalarını tanımlayabilirsiniz. Ayrıca, kodun hata ayıklama sürümlerini oluşturmak ve çalıştırmak için mantık hataları ve anlam hataları gibi çalışma zamanı hatalarını algılayabilir ve düzeltebilirsiniz.

 Tam olarak geliştirdiyseniz ve bir proje ya da çözüme yeterince hata ayıklaması uyguladığınızda, bileşenlerini bir yayın derlemesi içinde derleyebilirsiniz. Varsayılan olarak, bir yayın derlemesi en iyi duruma getirilir ve daha küçük olacak şekilde tasarlanmıştır ve hata ayıklama sürümünden daha hızlı çalışır. Daha fazla bilgi için bkz. [Izlenecek yol: uygulama oluşturma](../ide/walkthrough-building-an-application.md).

## <a name="choosing-a-build-method"></a>Yapı yöntemi seçme
 IDE 'deki varsayılan yapı seçeneklerini kullanarak, bir komut isteminde veya Team Foundation Build ' i kullanarak bir uygulama oluşturabilirsiniz. Bu seçeneklerin her biri, temel alınan teknoloji olarak MSBuild kullanır ve aşağıdaki tabloda gösterildiği gibi her yaklaşımın belirli avantajları vardır.

|Build yöntemi|Yararları|Daha fazla bilgi edinmek için|
|------------------|--------------|--------------------------|
|IDE 'yi kullanma|-Derlemeleri hemen kolayca oluşturup çalıştırabilirsiniz.<br />-C++ ve C# projeleri için çok işlemcili derlemeler çalıştırabilirsiniz.<br />-Derleme sisteminin bazı yönlerini özelleştirebilirsiniz.|[Visual Studio'da Projeler ve Çözümler Oluşturma ve Temizleme](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)|
|MSBuild komut satırı çalıştırma|-Visual Studio 'Yu yüklemeden projeler oluşturabilirsiniz.<br />-Tüm proje türleri için çok işlemcili derlemeler çalıştırabilirsiniz.<br />-Yapı sisteminin birçok alanını özelleştirebilirsiniz.|[MSBUILD](../msbuild/msbuild.md)|
|Team Foundation Build kullanma|-Yapı işleminizi otomatikleştirebilir. Örneğin, her bir veya daha fazla projeyi her bir kod iade edildiğinde her gece veya bir kez oluşturabilirsiniz. Ayrıca, geliştirme bilgisayarınızda değil, paylaşılan yapı sunucularında projeler de oluşturabilirsiniz.<br />-Derlemek istediğiniz kodu, çalıştırmak istediğiniz testleri ve diğer yaygın seçenekleri hızlıca belirtebilirsiniz.<br />-Derleme iş akışını değiştirebilir ve gerektiğinde, derin özelleştirilmiş görevler gerçekleştirmek için derleme etkinlikleri oluşturabilirsiniz.|[Uygulama oluşturma](/azure/devops/pipelines/index)|

## <a name="building-from-the-ide"></a>IDE 'den oluşturma
 Bir proje oluşturduğunuzda, varsayılan derleme yapılandırmaları kendisi için tanımlanır ve yapılar için bağlam sağlamak üzere buna bir çözüm derleme yapılandırması atanır. Çözüm konfigürasyonları, çözümdeki projelerin nasıl oluşturulup dağıtıldığını tanımlar. Proje konfigürasyonları, bir platform ve derleme türü (örneğin, Win32 sürümü) için benzersiz olan bir proje özellikleri kümesidir. Bu varsayılan konfigürasyonları düzenleyebilir ve kendi yapılandırmalarınızı oluşturabilirsiniz. Daha fazla bilgi için bkz. [Proje tasarımcısına giriş](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7) ve [nib nasıl yapılır: proje özelliklerini ve yapılandırma ayarlarını değiştirme](https://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67).

 IDE içinden aşağıdaki ek görevleri gerçekleştirebilirsiniz:

- [Derleme çıkış dizinini değiştirin](../ide/how-to-change-the-build-output-directory.md).

- [Doğru bir şekilde derlemek için başka bir projeden çıktıya bağımlı olan projeleri belirler](../ide/how-to-create-and-remove-project-dependencies.md).

- [Derlemeler için derleme günlüğü veya çıkış penceresinde bulunan bilgi miktarını değiştirin](../ide/how-to-view-save-and-configure-build-log-files.md).

- [Visual C#, Visual C++ veya Visual Basic için belirli derleyici uyarılarını gizleyin](../ide/how-to-suppress-compiler-warnings.md).

- [Derleme için özel derleme öncesi ve derleme sonrası eylemleri belirtin](../ide/specifying-custom-build-events-in-visual-studio.md).

- Paralel derlemeler kullanarak derleme performansını geliştirin. Daha fazla bilgi için bkz. [paralel olarak birden çok proje oluşturma](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) veya Web günlüğü gönderi [ayarlama C++ derleme paralelliği](https://blogs.msdn.microsoft.com/msbuild/2010/03/07/tuning-c-build-parallelism-in-vs2010/).

## <a name="see-also"></a>Ayrıca Bkz.
 [Izlenecek yol: uygulama oluşturma](../ide/walkthrough-building-an-application.md) [derleme yapılandırmalarının](../ide/understanding-build-configurations.md) yanı sıra [derleme platformlarını anlama](../ide/understanding-build-platforms.md) [(derleme) Web sitesi projelerini oluşturma (derleme)](https://msdn.microsoft.com/library/a9cbb88c-8fff-4c67-848b-98fbfd823193) [: Proje bağımlılıklarını oluşturma ve kaldırma](../ide/how-to-create-and-remove-project-dependencies.md)
