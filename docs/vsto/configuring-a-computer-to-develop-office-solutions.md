---
title: Office çözümleri geliştirmek için bir bilgisayarı yapılandırma
description: Visual Studio, .NET Framework ve Microsoft Office desteklenen bir sürümünü nasıl yükleyebileceğinizi öğrenin ve böylece Microsoft Office için VSTO eklentiler ve özelleştirmeler oluşturabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 7c74dca2c88538ddb0ddb17938ca50f3ab831276
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634174"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Office çözümleri geliştirmek için bir bilgisayarı yapılandırma

Microsoft Office için VSTO eklentiler ve özelleştirmeler oluşturmak üzere Visual Studio, .NET Framework ve Microsoft Office desteklenen bir sürümünü yüklemelisiniz.

|Yazılım|Desteklenen sürümler|
|--------------|------------------------|
|Visual Studio 2017| **Office/SharePoint geliştirme** iş yüküyle herhangi bir sürüm.|
|.NET Framework|-.NET Framework 4 veya üzeri.|
|Microsoft Office|<ul><li>kurumsal Microsoft 365 uygulamalar dahil Office herhangi bir suite sürümü.</li><li>Aşağıdaki tek başına uygulamalardan herhangi biri:<br /><br /> <ul><li>Excel</li><li>ınfopath (yalnızca Office 2013 ve Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Project</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic for Applications (VBA), Office bir parçası olarak yüklenmelidir. **Önemli:** Office 2010 uygulamaları için tıkla-çalıştır sürümleri desteklenmez.|

ayrıntılı yükleme adımları için bkz. [nasıl yapılır: bilgisayarı yapılandırma Office çözümleri geliştirme](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Proje şablonları görünmezse veya Visual Studio içinde çalışmadıklarında

Visual Studio, .NET Framework ve Microsoft Office desteklenen bir sürümünü yüklerseniz, ancak Office proje şablonları Visual Studio **yeni Project** iletişim kutusunda görünmez ya da bir hata alırsanız, şunu denetleyin:

- bilgisayarınızda Microsoft Office geliştirici araçlarının yüklü olduğundan emin olun.

     Office geliştirici araçları Visual Studio isteğe bağlı bir bileşenidir, ancak Visual Studio birlikte otomatik olarak yüklenir. yüklenecek özellikleri belirterek Visual Studio yüklemesini özelleştirirseniz, araçları yüklemek için kurulum sırasında **Microsoft Office Geliştirici Araçları** ' yı seçtiğinizden emin olun.

     bu araçların yüklendiğinden emin olmak için Visual Studio kurulum programını başlatın ve **değiştir** düğmesini seçin. **Microsoft Office Geliştirici Araçları** onay kutusunu seçin ve ardından **güncelleştir** düğmesini seçin.

- ' ın tıkla-çalıştır tarafından teslim edilen bir Office sürümünü çalıştırdığınızdan emin olun. bkz. [nasıl yapılır: Outlook bir bilgisayarda bir tıkla-çalıştır uygulaması olup olmadığını doğrulama](/previous-versions/office/developer/office-2010/ff864733(v=office.14)).

- Microsoft Office yalnızca bir sürümünü çalıştırıyor olduğunuzdan emin olun.

sorun yaşamaya devam ederseniz, bkz. [Office çözümlerinde hatalara yönelik ek destek](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio &#40;Office geliştirmeye başlayın&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [nasıl yapılır: Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [nasıl yapılır: Office için Visual Studio Araçları çalışma zamanı yeniden dağıtılabilir](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [nasıl yapılır: birincil birlikte çalışma derlemelerini Office yüklemesi](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Office uygulama ve proje türü tarafından kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md)