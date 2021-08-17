---
title: Çözümleri farklı sürümlerde Microsoft Office
description: Visual Studio 2010 ve üzeri kullanılarak oluşturulan Microsoft Office çözüm sürümlerini nasıl çalıştırabilirsiniz?
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], multiple Office versions
- Office applications [Office development in Visual Studio], multiple Office versions
- Office development in Visual Studio, multiple Office versions
- Office solutions [Office development in Visual Studio]
- multiple Office versions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 5822119057071884d3abf64242ca73371daeff1d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025790"
---
# <a name="run-solutions-in-different-versions-of-microsoft-office"></a>Çözümleri farklı sürümlerde Microsoft Office

## <a name="run-office-solutions-created-by-using-visual-studio-2010-and-above"></a>2010 ve üzeri Office kullanılarak oluşturulan Visual Studio çözümlerini çalıştırın

|Proje Office hedeflenen uygulamanın sürümü|Proje .NET Framework<sup>1'in hedef hedefi</sup>|Çözümü Office sürümlerinin sürümleri|Son kullanıcı bilgisayarda gerekli çalışma zamanı|
|--------------------------------------------------------|------------------------------------------------------|--------------------------------------------------|-------------------------------------------|
|Office 2016 ve[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonraki bir|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office sistem<sup>2</sup>|Office Çalışma Zamanı için Visual Studio 2010 Araçları|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonraki bir|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office sistem<sup>2</sup>|Office Çalışma Zamanı için Visual Studio 2010 Araçları|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|.NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Office Çalışma Zamanı için Visual Studio 2010 Araçları|
|2007 Microsoft Office sistemi|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonraki bir süre sonra,<br /><br /> veya<br /><br /> .NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office sistemi|Office Çalışma Zamanı için Visual Studio 2010 Araçları|

 1. Çözüm .NET Framework çalışması için son kullanıcı bilgisayarlarında projenizin hedeflemektedir. Örneğin, projeniz .NET Framework 3.5'i hedeflerse, .NET Framework 3.5 son kullanıcı bilgisayarlarında gereklidir. Bu örnekte, yalnızca son kullanıcı bilgisayarlarında [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] yüklüyse çözümünüz çalışmaz.

 2. Bu senaryoda, çözüm 2007 Microsoft Office sistemi yalnızca 'de yeni olan özellikleri kullanmazsa hatasız olarak çalışmasına neden [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] olur.

## <a name="run-office-solutions-created-by-using-versions-of-visual-studio-prior-to-visual-studio-2010"></a>2010 Office önceki Visual Studio sürümleri kullanılarak oluşturulan Visual Studio çözümlerini çalıştırın
 Microsoft Office uygulamaları, 2010'dan önceki Visual Studio sürümleri kullanılarak oluşturulan Visual Studio çalıştırabilirsiniz. Bazı durumlarda, bu çözümler farklı sürümlerini [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] gerektirir. farklı sürümleri [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] aynı bilgisayara yan yana yükleyebilir.

 Aşağıdaki tabloda, Microsoft Office önceki Visual Studio kullanılarak oluşturulan çözümlerin hangi sürümlerini çalıştırabilirsiniz ve her çözüm için hangi ve .NET Framework sürümlerinin [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] gerekli olduğu gösterir.

|Çözümü Visual Studio için kullanılan Visual Studio sürümü|Proje Office hedeflenen uygulamanın sürümü|Çözümü Office sürümlerinin sürümleri|Son kullanıcı bilgisayarda gerekli çalışma zamanı|Son .NET Framework bilgisayarda gerekli sürüm|
|----------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|-------------------------------------------|----------------------------------------------------------|
|Visual Studio 2008 Professional<br /><br /> veya<br /><br /> Visual Studio Team System 2008|2007 Microsoft Office sistemi|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] <sup>1</sup><br /><br /> 2007 Microsoft Office sistemi|Visual Studio Runtime 1 için Office 2010<sup>Araçları</sup><br /><br /> veya<br /><br /> Visual Studio Araçları sistemi için Microsoft Office (sürüm 3.0 Çalışma Zamanı)|.NET Framework 3.5|
|VSTO 2005 SE 2 yüklü olan Visual Studio 2005'in aşağıdaki<sup>sürümlerinden</sup> biri:<br /><br /> - Visual Studio için 2005 Office<br />- Visual Studio Team System 2005<br />- Visual Studio 2005 Professional|2007 Microsoft Office sistemi|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (yalnızca 32 bit<sup>3)</sup><br /><br /> 2007 Microsoft Office sistemi|Visual Studio Second Edition Runtime için Office 2005 Araçları|.NET Framework 2.0, .NET Framework 3.0 veya .NET Framework 3.5|
|Aşağıdaki sürümlerden herhangi biri Visual Studio:<br /><br /> - Visual Studio 2008 Professional<br />- Visual Studio Team System 2008<br />- Visual Studio 2005 Office Araçları (VSTO 2005 SE<sup>2</sup> yüklü veya yüklü değil)<br />- Visual Studio Team System 2005 (VSTO 2005 SE<sup>2</sup> yüklü veya yüklü değil)<br />- Visual Studio VSTO 2005 Professional 2005 SE<sup>2005</sup> sürümü yüklü|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (yalnızca 32 bit<sup>3)</sup><br /><br /> 2007 Microsoft Office sistemi<br /><br /> Microsoft Office 2003|Visual Studio Second Edition Runtime için Office 2005 Araçları|.NET Framework 2.0, .NET Framework 3.0 veya .NET Framework 3.5|

 1. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] uygulamaları, Visual Studio için 2010 Araçları'Office içerir. Bu nedenle, bu uygulamalar bu senaryoda Microsoft Office sistemi (sürüm 3.0 Çalışma Zamanı) için Visual Studio Araçları yerine Office çalışma zamanı için Visual Studio 2010 Araçlarını kullanır. 2007 Microsoft Office sistemi uygulamaları Office Runtime için Visual Studio 2010 Araçlarını veya Microsoft Office sistemi için Visual Studio Araçları 'i (sürüm 3.0 Çalışma Zamanı) kullanabilir.

 2. VSTO 2005 SE, Visual Studio 2003 ve 2007 Microsoft Office sistemi için Microsoft Office VSTO Eklenti proje şablonları sağlayan ücretsiz bir Microsoft Office eklentidir. Visual Studio 2005 Professional, Visual Studio 2005 Tools for Office veya Visual Studio Team System 2005'te bir sürümle yükleyebilirsiniz. Daha fazla bilgi için bkz. Visual Studio İkinci Sürüm için [2005 Office Araçları.](https://developer.microsoft.com/office/docs)

 3. Office Second Edition Runtime için Visual Studio 2005 Araçları gerektiren Office çözümleri, ve 'nin 64 bit sürümleriyle [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] uyumlu [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] değildir. Bu çözümleri veya 64 bitlik sürümlerinde çalıştırmak için projeyi 2007 veya 2007 Microsoft Office sistemini hedef alan bir [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] Visual Studio [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] 2008 projesine veya sürümüne Microsoft Office gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yeni çözümler tasarlama Office oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Office için Visual Studio Araçları çalışma zamanının genel bakışı](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Nasıl Office: Office projelerini Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Office için Visual Studio Araçları çalışma zamanı yükleme senaryoları](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
- [Yeni çözümler geliştirmek için bilgisayarı Office yapılandırma](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
