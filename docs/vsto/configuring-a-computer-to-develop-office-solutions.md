---
title: Office çözümleri geliştirmek için bir bilgisayarı yapılandırma
description: Microsoft Office için VSTO eklentileri ve özelleştirmeleri oluşturabilmek için Visual Studio 'nun desteklenen bir sürümünü, .NET Framework ve Microsoft Office nasıl yükleyebileceğinizi öğrenin.
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
ms.workload:
- office
ms.openlocfilehash: ee8f840aa81d3decfdb96dd2658b758704443347
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910568"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Office çözümleri geliştirmek için bir bilgisayarı yapılandırma

Microsoft Office için VSTO eklentileri ve özelleştirmeleri oluşturmak için, Visual Studio 'nun desteklenen bir sürümünü, .NET Framework ve Microsoft Office yüklemeyi yapın.

|Yazılım|Desteklenen sürümler|
|--------------|------------------------|
|Visual Studio 2017| **Office/SharePoint geliştirme** iş yüküyle herhangi bir sürüm.|
|.NET Framework|-.NET Framework 4 veya üzeri.|
|Microsoft Office|<ul><li>Office 'in kuruluş için Microsoft 365 uygulamalar dahil tüm paket sürümleri.</li><li>Aşağıdaki tek başına uygulamalardan herhangi biri:<br /><br /> <ul><li>Excel</li><li>InfoPath (yalnızca Office 2013 ve Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Project</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic for Applications (VBA), Office 'in bir parçası olarak yüklenmelidir. **Önemli:** Office 2010 uygulamaları 'nın Tıkla-Çalıştır sürümleri desteklenmez.|

Ayrıntılı yükleme adımları için bkz. [nasıl yapılır: bilgisayarı Office çözümleri geliştirmek üzere yapılandırma](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Proje şablonları görünmezse veya Visual Studio 'da çalışmadıklarında

Visual Studio 'nun desteklenen bir sürümünü, .NET Framework ve Microsoft Office yüklerseniz, ancak Office proje şablonları Visual Studio **Yeni proje** iletişim kutusunda görünmez veya bir hata alırsanız, aşağıdakileri kontrol edin:

- Bilgisayarınızda Microsoft Office Geliştirici araçlarının yüklü olduğundan emin olun.

     Office geliştirici araçları, Visual Studio 'nun isteğe bağlı bir bileşenidir, ancak Visual Studio ile birlikte otomatik olarak yüklenir. Yüklenecek özellikleri belirterek Visual Studio yüklemesini özelleştirirseniz, araçları yüklemek için kurulum sırasında **Microsoft Office geliştirici araçları** seçtiğinizden emin olun.

     Bu araçların yüklendiğinden emin olmak için Visual Studio Kurulum programını başlatın ve **Değiştir** düğmesini seçin. **Microsoft Office geliştirici araçları** onay kutusunu seçin ve ardından **Güncelleştir** düğmesini seçin.

- Office 'in Tıkla-Çalıştır ile sunulan bir sürümünü çalıştırdığınızdan emin olun. Bkz. [nasıl yapılır: Outlook 'un bir bilgisayarda bir Tıkla-Çalıştır uygulaması olup olmadığını doğrulama](/previous-versions/office/developer/office-2010/ff864733(v=office.14)).

- Microsoft Office yalnızca bir sürümünü çalıştırıyor olduğunuzdan emin olun.

Sorun yaşamaya devam ederseniz, bkz. [Office çözümlerinde hatalar Için ek destek](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio 'da Office geliştirme &#40;kullanmaya başlama&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Nasıl yapılır: Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Nasıl yapılır: Office çalışma zamanı yeniden dağıtılabilir için Visual Studio Araçları yüklemesi](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Nasıl yapılır: Office birincil birlikte çalışma derlemelerini yüklemek](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Office uygulaması ve proje türü tarafından kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md)