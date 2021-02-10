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
ms.workload:
- office
ms.openlocfilehash: f9083a92482a99d7ec7ecce144ece2806e9889e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961397"
---
# <a name="run-solutions-in-different-versions-of-microsoft-office"></a>Farklı Microsoft Office sürümlerinde çözüm çalıştırma

## <a name="run-office-solutions-created-by-using-visual-studio-2010-and-above"></a>Visual Studio 2010 ve üzeri kullanılarak oluşturulan Office çözümlerini çalıştırın

|Proje şablonu tarafından hedeflenen Office sürümü|Projenin hedef .NET Framework<sup>1</sup>|Çözümü çalıştırabilirler Office sürümleri|Son Kullanıcı bilgisayarında gerekli çalışma zamanı|
|--------------------------------------------------------|------------------------------------------------------|--------------------------------------------------|-------------------------------------------|
|Office 2016 ve [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office sistem<sup>2</sup>|Office Çalışma Zamanı için Visual Studio 2010 Araçları|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office sistem<sup>2</sup>|Office Çalışma Zamanı için Visual Studio 2010 Araçları|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|.NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Office Çalışma Zamanı için Visual Studio 2010 Araçları|
|2007 Microsoft Office sistemi|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri,<br /><br /> veya<br /><br /> .NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office sistemi|Office Çalışma Zamanı için Visual Studio 2010 Araçları|

 1. Çözümünüzün çalışması için, son kullanıcı bilgisayarlarında projenizin hedeflediği .NET Framework sürümü gerekir. Örneğin, projeniz 3,5 .NET Framework hedefliyorsa, son kullanıcı bilgisayarlarında 3,5 .NET Framework gerekir. Bu örnekte, çözümünüz yalnızca [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] son kullanıcı bilgisayarlarında yüklüyse çalışmaz.

 2. Bu senaryoda çözüm, yalnızca içinde yeni olan özellikleri kullanmıyorsa 2007 Microsoft Office sisteminde hata olmadan çalışır [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] .

## <a name="run-office-solutions-created-by-using-versions-of-visual-studio-prior-to-visual-studio-2010"></a>Visual Studio 2010 öncesi Visual Studio sürümlerini kullanarak oluşturulan Office çözümlerini çalıştırın
 Microsoft Office uygulamalar, Visual Studio 2010 öncesi Visual Studio sürümleri kullanılarak oluşturulan çözümleri çalıştırabilir. Bazı durumlarda, bu çözümler farklı sürümlerini gerektirir [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Farklı sürümleri [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] aynı bilgisayarda yan yana yüklenebilir.

 Aşağıdaki tabloda, hangi Microsoft Office sürümlerinin, Visual Studio 'nun önceki sürümleri kullanılarak oluşturulan çözümlerin çalıştırılabileceği ve [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] her bir çözüm için ve .NET Framework sürümlerinin gerekli olduğu gösterilmektedir.

|Çözümü oluşturmak için kullanılan Visual Studio sürümü|Proje şablonu tarafından hedeflenen Office sürümü|Çözümü çalıştırabilirler Office sürümleri|Son Kullanıcı bilgisayarında gerekli çalışma zamanı|Son Kullanıcı bilgisayarında gerekli .NET Framework sürümü|
|----------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|-------------------------------------------|----------------------------------------------------------|
|Visual Studio 2008 Professional<br /><br /> veya<br /><br /> Visual Studio Team System 2008|2007 Microsoft Office sistemi|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] <sup>1</sup><br /><br /> 2007 Microsoft Office sistemi|Office çalışma zamanı<sup>1</sup> Için Visual Studio 2010 araçları<br /><br /> veya<br /><br /> Microsoft Office sistemi için Visual Studio Araçları (sürüm 3,0 çalışma zamanı)|.NET Framework 3.5|
|VSTO 2005 so<sup>2</sup> Ile Visual Studio 2005 ' nin aşağıdaki sürümlerinden biri yüklendi:<br /><br /> -Office için Visual Studio 2005 araçları<br />-Visual Studio Team System 2005<br />-Visual Studio 2005 Professional|2007 Microsoft Office sistemi|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (32-bit yalnızca<sup>3</sup>)<br /><br /> 2007 Microsoft Office sistemi|Office için Visual Studio 2005 araçları Ikinci sürüm çalışma zamanı|.NET Framework 2,0, .NET Framework 3,0 veya .NET Framework 3,5|
|Aşağıdaki Visual Studio sürümlerinden herhangi biri:<br /><br /> -Visual Studio 2008 Professional<br />-Visual Studio Team System 2008<br />-Office için Visual Studio 2005 araçları (VSTO 2005<sup>2</sup> . sürüm yüklü olan veya olmayan)<br />-Visual Studio Team System 2005 (VSTO 2005<sup>2</sup> ' de yüklü olan veya olmayan)<br />-VSTO 2005<sup>2</sup> . sürüm yüklü Visual Studio 2005 Professional|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (32-bit yalnızca<sup>3</sup>)<br /><br /> 2007 Microsoft Office sistemi<br /><br /> Microsoft Office 2003|Office için Visual Studio 2005 araçları Ikinci sürüm çalışma zamanı|.NET Framework 2,0, .NET Framework 3,0 veya .NET Framework 3,5|

 1. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] uygulamalar, Office çalışma zamanı Için Visual Studio 2010 araçlarını içerir. Bu nedenle bu uygulamalar, bu senaryoda Microsoft Office sistemi (sürüm 3,0 çalışma zamanı) Visual Studio Araçları değil, her zaman Office çalışma zamanı için Visual Studio 2010 araçları 'nı kullanır. 2007 Microsoft Office sistemindeki uygulamalar, Office çalışma zamanı için Visual Studio 2010 araçları veya Microsoft Office sistemi için Visual Studio Araçları (sürüm 3,0 çalışma zamanı) kullanabilir.

 2. VSTO 2005, Microsoft Office 2003 ve 2007 Microsoft Office sistemi için VSTO eklentisi proje şablonları sağlayan ücretsiz bir Visual Studio eklentisi. Visual Studio 2005 Professional, Office için Visual Studio 2005 araçları veya Visual Studio Team System 2005 sürümü ile yüklenebilir. Daha fazla bilgi için bkz. [Office Için Visual Studio 2005 araçları Second Edition](https://developer.microsoft.com/office/docs).

 3. Office Second Edition çalışma zamanı için Visual Studio 2005 araçları gerektiren Office çözümleri, ve ' nin 64 bit sürümleriyle uyumlu değildir [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] . Bu çözümleri veya uygulamasının 64 bitlik sürümünde çalıştırmak için [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] , projeyi [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] veya 2007 Microsoft Office sistemini hedefleyen bir Visual Studio 2008 projesine yükseltmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Nasıl yapılır: Visual Studio 'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Office çalışma zamanı yükleme senaryoları için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
- [Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
