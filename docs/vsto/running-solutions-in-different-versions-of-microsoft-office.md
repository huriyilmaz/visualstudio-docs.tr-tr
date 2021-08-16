---
title: Farklı Microsoft Office sürümlerinde çözüm çalıştırma
description: Visual Studio 2010 ve üzeri kullanılarak oluşturulan Microsoft Office çözümlerin sürümlerini nasıl çalıştırabileceğinizi öğrenin.
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
ms.openlocfilehash: 65d3338307668ce07b2a08aa7bc2f97ab3b09fbd1280767e06ad897194a58272
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121408192"
---
# <a name="run-solutions-in-different-versions-of-microsoft-office"></a>Farklı Microsoft Office sürümlerinde çözüm çalıştırma

## <a name="run-office-solutions-created-by-using-visual-studio-2010-and-above"></a>Visual Studio 2010 ve üzeri kullanılarak oluşturulan Office çözümlerini çalıştırın

|proje şablonu tarafından hedeflenen Office sürümü|projenin hedef .NET Framework<sup>1</sup>|çözümü çalıştırabilirler Office sürümleri|Son Kullanıcı bilgisayarında gerekli çalışma zamanı|
|--------------------------------------------------------|------------------------------------------------------|--------------------------------------------------|-------------------------------------------|
|Office 2016 ve[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office sistem<sup>2</sup>|Office Çalışma Zamanı için Visual Studio 2010 Araçları|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office sistem<sup>2</sup>|Office Çalışma Zamanı için Visual Studio 2010 Araçları|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|.NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Office Çalışma Zamanı için Visual Studio 2010 Araçları|
|2007 Microsoft Office sistemi|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri,<br /><br /> veya<br /><br /> .NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office sistemi|Office Çalışma Zamanı için Visual Studio 2010 Araçları|

 1. çözümünüzün çalışması için, son kullanıcı bilgisayarlarında projenizin hedeflediği .NET Framework sürümü gerekir. örneğin, projeniz 3,5 .NET Framework hedefliyorsa, son kullanıcı bilgisayarlarında 3,5 .NET Framework gerekir. Bu örnekte, çözümünüz yalnızca [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] son kullanıcı bilgisayarlarında yüklüyse çalışmaz.

 2. bu senaryoda çözüm, yalnızca içinde yeni olan özellikleri kullanmıyorsa 2007 Microsoft Office sisteminde hata olmadan çalışır [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] .

## <a name="run-office-solutions-created-by-using-versions-of-visual-studio-prior-to-visual-studio-2010"></a>Visual Studio 2010 ' den önceki Visual Studio sürümleri kullanılarak oluşturulan Office çözümlerini çalıştırın
 Microsoft Office uygulamalar, Visual Studio 2010 ' den önceki Visual Studio sürümleri kullanılarak oluşturulan çözümleri çalıştırabilir. Bazı durumlarda, bu çözümler farklı sürümlerini gerektirir [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Farklı sürümleri [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] aynı bilgisayarda yan yana yüklenebilir.

 aşağıdaki tabloda, hangi Microsoft Office sürümlerinin Visual Studio önceki sürümleri kullanılarak oluşturulan çözümlerin ve [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] her çözüm için hangi ve .NET Framework sürümlerinin gerekli olduğu gösterilmektedir.

|çözümü oluşturmak için kullanılan Visual Studio sürümü|proje şablonu tarafından hedeflenen Office sürümü|çözümü çalıştırabilirler Office sürümleri|Son Kullanıcı bilgisayarında gerekli çalışma zamanı|son kullanıcı bilgisayarında gerekli .NET Framework sürümü|
|----------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|-------------------------------------------|----------------------------------------------------------|
|Visual Studio 2008 Professional<br /><br /> veya<br /><br /> Visual Studio Team System 2008|2007 Microsoft Office sistemi|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] <sup>1</sup><br /><br /> 2007 Microsoft Office sistemi|Office Runtime<sup>1</sup> için Visual Studio 2010 araçları<br /><br /> veya<br /><br /> Microsoft Office sistemi için Visual Studio Araçları (sürüm 3,0 çalışma zamanı)|.NET Framework 3.5|
|Visual Studio 2005 ' nin aşağıdaki sürümlerinden biri VSTO 2005 SE<sup>2</sup> yüklendi:<br /><br /> -Office için Visual Studio 2005 araçları<br />-Visual Studio Team System 2005<br />-Visual Studio 2005 Professional|2007 Microsoft Office sistemi|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (32-bit yalnızca<sup>3</sup>)<br /><br /> 2007 Microsoft Office sistemi|Office ikinci sürüm çalışma zamanı için Visual Studio 2005 araçları|.NET Framework 2,0, .NET Framework 3,0 veya .NET Framework 3,5|
|Aşağıdaki Visual Studio sürümlerinden herhangi biri:<br /><br /> -Visual Studio 2008 Professional<br />-Visual Studio Team System 2008<br />-Office için Visual Studio 2005 araçları (VSTO 2005 SE<sup>2</sup> yüklü olan veya olmadan)<br />-Visual Studio Team System 2005 (VSTO 2005 SE<sup>2</sup> yüklü veya olmadan)<br />-Visual Studio 2005 Professional VSTO 2005 SE<sup>2</sup> yüklendi|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (32-bit yalnızca<sup>3</sup>)<br /><br /> 2007 Microsoft Office sistemi<br /><br /> Microsoft Office 2003|Office ikinci sürüm çalışma zamanı için Visual Studio 2005 araçları|.NET Framework 2,0, .NET Framework 3,0 veya .NET Framework 3,5|

 1. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] uygulamalar, Office çalışma zamanına yönelik Visual Studio 2010 araçlarını içerir. bu nedenle bu uygulamalar her zaman, bu senaryoda Microsoft Office sistemi (sürüm 3,0 çalışma zamanı) Visual Studio Araçları yerine Office çalışma zamanı için Visual Studio 2010 araçlarını kullanır. 2007 Microsoft Office sistemindeki uygulamalar Office çalışma zamanı için Visual Studio 2010 araçlarını veya Microsoft Office sistemi (sürüm 3,0 çalışma zamanı) için Visual Studio Araçları kullanabilir.

 2. VSTO 2005 SE, Microsoft Office 2003 ve 2007 Microsoft Office sistemi için VSTO eklenti proje şablonları sağlayan ücretsiz bir Visual Studio eklentisi. Visual Studio 2005 Professional, Office Visual Studio 2005 araçları veya Visual Studio Team System 2005 sürümü ile yüklenebilir. daha fazla bilgi için bkz. [Office ikinci sürüm için Visual Studio 2005 araçları](https://developer.microsoft.com/office/docs).

 3. Office ikinci sürüm çalışma zamanı için Visual Studio 2005 araçları gerektiren Office çözümleri, ve 64 bit sürümleriyle uyumlu değildir [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] . bu çözümleri veya uygulamasının 64 bitlik sürümünde çalıştırmak için [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] , projeyi [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] veya 2007 Microsoft Office sistemini hedefleyen Visual Studio 2008 projesine yükseltmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Office için Visual Studio Araçları çalışma zamanına genel bakış](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [nasıl yapılır: Visual Studio Office projeler oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Office için Visual Studio Araçları çalışma zamanı yükleme senaryoları](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
- [Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
