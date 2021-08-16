---
title: Office için Visual Studio Araçları çalışma zamanı yükleme senaryoları
description: Office çalışma zamanı için Visual Studio 2010 Araçları'Office öğrenin. Bu makalede üç yükleme senaryosu açıklanmıştır.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, installation scenarios
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 4869314ef51dbfdcdb73d3a44578b689425f8647ce30b63c67fbd090bd2740ae
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384112"
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Office için Visual Studio Araçları çalışma zamanı yükleme senaryoları

  Office için Visual Studio 2010 Araçları'Office üç şekilde yükleyebilirsiniz:

- yüklemesi Visual Studio.

- yüklemesi Microsoft Office.

- Office için Visual Studio 2010 Araçları'Office yeniden dağıtılabilir.

  Yüklü çalışma zamanı bileşenleri, bilgisayarın yapılandırmasına ve yükleme senaryosuna bağlıdır.

## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Her yükleme senaryosunda yüklü çalışma zamanı bileşenleri

 Visual Studio için Office 2010 Araçları'nın üç bileşeni vardır: Office çözüm yükleyicisi, .NET Framework 3.5 için Office uzantıları ve veya sonraki sürümü için Office [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] uzantıları. Çalışma zamanı yüklenirken, Office çözüm yükleyicisi her zaman yüklenir. Uygulama için Office uzantılarının .NET Framework, bilgisayarın yapılandırmasına ve yükleme senaryosuna bağlıdır. Çalışma zamanı ilk Office uzantılardan biri yükleneyse, belirli gereksinimler karşılandı olduğunda çalışma zamanı eksik Office uzantılarını otomatik olarak yükleyene kadar devam eder. Çalışma zamanının bu özelliği, isteğe bağlı *yükleme olarak adlandırılan bir özelliktir.*

 Aşağıdaki tabloda, her çalışma zamanı yükleme senaryosunda varsayılan olarak hangi çalışma zamanı bileşenlerinin yüklü olduğu gösterir. Her senaryo hakkında daha fazla bilgi daha sonra görünür.

|Çalışma zamanı yükleme senaryosu|Office çözüm yükleyicisi|Office 3.5 .NET Framework uzantıları|Office uzantıları[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|Office uzantıları[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|
|-----------------------------------|----------------------------|--------------------------------------------------| - |---------------------------------------------------------------------------|
|ve [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] sonraki ile|Yes|Evet, .NET Framework 3.5 zaten yüklüyse.|Yes|Yes|
|Ile [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Yes|Evet, .NET Framework 3.5 zaten yüklüyse.|Hayır|Hayır|
|Office 2010 Service Pack 1 (SP1) veya sonraki bir|Yes|Evet, .NET Framework 3.5 zaten yüklüyse.|Evet, zaten [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] yüklüyse.|Hayır|
|2013 Office ve daha yeni sürümlerle|Yes|Evet, .NET Framework 3.5 zaten yüklüyse|Evet, zaten [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] yüklüyse.|Evet, zaten [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] yüklüyse.|
|Yeniden dağıtılabilir çalışma zamanı ile|Yes|Evet, .NET Framework 3.5 zaten yüklüyse|Evet, zaten [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] yüklüyse.|Evet, zaten [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] yüklüyse.|

### <a name="install-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Çalışma zamanının yüklemesini Visual Studio veya Microsoft Office Geliştirici Araçları için Visual Studio

 Office geliştirici araçlarını Visual Studio, ve için Office uzantıları her zaman geliştirme [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] bilgisayarına yüklenir. Office 3.5 için .NET Framework uzantıları yalnızca .NET Framework 3.5 geliştirme bilgisayarda mevcutsa yüklenir. .NET Framework 3.5'i yükledikten sonra, çalışma zamanı .NET Framework 3.5'i hedef alan bir Office .NET Framework projesi 3.5'e yönelik Office uzantılarını otomatik olarak [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] yüklenir.

> [!WARNING]
> veya sonraki bir Office kullanarak .NET Framework 3.5'i hedef alan bir proje [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] oluşturamazsiniz.

 Office geliştirici araçlarını yükleme hakkında daha fazla bilgi için, bkz. Nasıl yapılandırılır: Bir bilgisayarı yazılım [Office yapılandırma.](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)

### <a name="install-the-runtime-with-office"></a>Çalışma zamanlarını Office

 Office'i Office 3.5 yüklüyse .NET Framework 3.5 için .NET Framework uzantıları yüklenir. Office'den sonra .NET Framework 3.5'i yüklemeniz, bir Office uygulamasının .NET Framework 3.5'i hedef alan bir çözümü ilk kez yüklemesi sırasında .NET Framework 3.5 için Office uzantılarını otomatik olarak yüklenir.

 veya Office için uzantılar, ilgili Office sürümleri bilgisayarda zaten varsa .NET Framework [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ile birlikte yüklenir.

 Kullanıcılarının, uygulamanızı kullanmak için gerekli uzantılara sahip olduğundan emin olmak için çözümünüz için önkoşul olarak Visual Studio 2010 Araçları'nın en son sürümünü Office çalışma zamanı yeniden dağıtılabilir olarak dahil edin. Önkoşullar hakkında daha fazla bilgi için [bkz. Office çözümü önkoşulları.](/previous-versions/bb608617(v=vs.110))

### <a name="install-the-runtime-by-using-the-runtime-redistributable"></a>Yeniden dağıtılabilir çalışma zamanı kullanarak çalışma zamanı yükleme

 Office çalışma zamanı yeniden dağıtılabilir için Visual Studio 2010 Araçları'nın el ile veya bir Office çözümü dağıtırken önkoşul olarak yeniden dağıtılabilir'i dahil kullanarak çalışma zamanı yükleyebilirsiniz.

 Office çalışma zamanı yeniden dağıtılabilir için Visual Studio 2010 Araçları'nın kullanılarak çalışma zamanının yüklemesi, .NET Framework 3.5 için Office uzantıları ve .NET Framework'nin ilgili sürümleri bilgisayarda zaten varsa veya sonraki sürümler için Office uzantıları [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] yüklenir. Çalışma zamanı yüklüyken bilgisayarın .NET Framework sürümlerinden biri eksikse, Office'nin eksik sürümüne .NET Framework uzantıları o anda yüklenmez. .NET Framework'nin eksik sürümünü daha sonra yükleyebiliyorsanız, uzantı gerektiren bir çözüm (çalışma zamanı ClickOnce kullanılarak dağıtılan bir çözümle yüklendiyse) veya (çalışma zamanı Windows Yükleyicisi kullanılarak dağıtılan bir çözümle yüklendiyse) sonraki sefer karşılık gelen Office uzantılarını otomatik olarak yüklenir.

 Önkoşulları bir ClickOnce dahil etmek hakkında daha fazla bilgi için, bkz. How [to: Install prerequisites](/previous-versions/bb608608(v=vs.110))on end user computers to run Office solutions . Yeniden dağıtılabilir paketten çalışma zamanının el ile nasıl yük olduğu hakkında daha fazla bilgi için [bkz. Nasıl yapılır: Yeniden](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)dağıtılabilir Office için Visual Studio Araçları yükleme.

## <a name="see-also"></a>Ayrıca bkz.

- [Office için Visual Studio Araçları çalışma zamanının genel bakışı](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Office için Visual Studio Araçları çalışma zamanında derlemeler](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
