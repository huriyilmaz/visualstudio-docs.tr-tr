---
title: Office için Visual Studio Araçları çalışma zamanı yükleme senaryoları
description: Office çalışma zamanına yönelik Visual Studio 2010 araçlarını nasıl yükleyebileceğinizi öğrenin. Bu makalede üç yükleme senaryosu açıklanmaktadır.
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
ms.openlocfilehash: 110e78b404ef5d25264a0e168bf9b6de5cad5d3c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122082692"
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Office için Visual Studio Araçları çalışma zamanı yükleme senaryoları

  Office çalışma zamanına yönelik Visual Studio 2010 araçlarını üç şekilde yükleyebilirsiniz:

- Visual Studio yüklediğinizde.

- Microsoft Office yüklediğinizde.

- Office çalışma zamanı yeniden dağıtılabilir için Visual Studio 2010 araçlarını yüklediğinizde.

  Yüklü çalışma zamanı bileşenleri bilgisayarın yapılandırmasına ve yükleme senaryosuna bağlıdır.

## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Her yükleme senaryosunda yüklü çalışma zamanı bileşenleri

 Office çalışma zamanına yönelik Visual Studio 2010 araçlarında üç bileşen vardır: Office çözüm yükleyicisi, .NET Framework 3,5 için Office uzantıları ve veya sonraki için Office uzantıları [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . çalışma zamanını yüklediğinizde Office çözüm yükleyicisi her zaman yüklenir. .NET Framework için Office uzantılarının yüklemesi bilgisayarın yapılandırmasına ve yükleme senaryosuna bağlıdır. çalışma zamanı ilk yüklendiğinde Office uzantılarından biri yüklenemezse, belirli gereksinimler karşılandığında çalışma zamanı eksik Office uzantılarını otomatik olarak yükler. Çalışma zamanının bu özelliğine *istek üzerine Install* adı verilir.

 Aşağıdaki tabloda, her çalışma zamanı yükleme senaryosunda varsayılan olarak hangi çalışma zamanı bileşenlerinin yüklendiği gösterilmektedir. Her senaryo hakkında daha fazla bilgi daha sonra görünür.

|Çalışma zamanı yükleme senaryosu|Office çözüm yükleyicisi|.NET Framework 3,5 için Office uzantıları|için Office uzantıları[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|için Office uzantıları[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|
|-----------------------------------|----------------------------|--------------------------------------------------| - |---------------------------------------------------------------------------|
|[!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]Ve sonraki sürümlerde|Yes|evet, .NET Framework 3,5 zaten yüklüyse.|Yes|Yes|
|Kullanılarak [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Yes|evet, .NET Framework 3,5 zaten yüklüyse.|Hayır|Hayır|
|Office 2010 Service Pack 1 (SP1) veya üzeri ile|Yes|evet, .NET Framework 3,5 zaten yüklüyse.|Evet, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] zaten yüklüyse.|Hayır|
|Office 2013 ve üzeri|Yes|evet, .NET Framework 3,5 zaten yüklüyse|Evet, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] zaten yüklüyse.|Evet, [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] zaten yüklüyse.|
|Yeniden dağıtılabilir çalışma zamanı|Yes|evet, .NET Framework 3,5 zaten yüklüyse|Evet, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] zaten yüklüyse.|Evet, [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] zaten yüklüyse.|

### <a name="install-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>çalışma zamanını Visual Studio veya Visual Studio için Microsoft Office Geliştirici Araçları olarak yükler

 Visual Studio Office geliştirici araçlarını yüklediğinizde, ve için Office uzantıları [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] her zaman geliştirme bilgisayarında yüklüdür. .NET Framework 3,5 Office uzantıları, yalnızca geliştirme bilgisayarında .NET Framework 3,5 zaten mevcutsa yüklenir. yüklendikten sonra 3,5 .NET Framework yüklerseniz [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] , .NET Framework 3,5 ' i hedefleyen bir Office projesi ilk kez oluşturduğunuzda çalışma zamanı .NET Framework 3,5 için Office uzantıları otomatik olarak yükler.

> [!WARNING]
> veya sonraki sürümünü kullanarak .NET Framework 3,5 hedefleyen bir Office projesi oluşturamazsınız [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] .

 Office geliştirici araçlarının nasıl yükleneceği hakkında daha fazla bilgi için bkz. [nasıl yapılır: bilgisayarı yapılandırma Office çözümleri geliştirme](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

### <a name="install-the-runtime-with-office"></a>Çalışma zamanını Office ile birlikte yükler

 Office yüklediğinizde, bilgisayarda .NET Framework 3,5 zaten varsa .NET Framework 3,5 Office uzantıları yüklenir. Office sonra 3,5 .NET Framework yüklerseniz, Office bir uygulama .NET Framework 3,5 ' i hedefleyen bir çözümü yüklemeye çalıştığında, çalışma zamanı .NET Framework 3,5 Office uzantıları otomatik olarak yükler.

 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]ayrıca, .NET Framework ilgili sürümleri bilgisayarda zaten mevcutsa, veya üzeri için Office uzantıları da Office yüklenir.

 kullanıcılarınızın uygulamanızı kullanmak için gerekli uzantılara sahip olduğundan emin olmak için, Office çalışma zamanı yeniden dağıtılabilir için Visual Studio 2010 araçlarının en son sürümünü çözümünüz için önkoşul olarak ekleyin. önkoşullar hakkında daha fazla bilgi için bkz. [dağıtım için Office çözüm önkoşulları](/previous-versions/bb608617(v=vs.110)).

### <a name="install-the-runtime-by-using-the-runtime-redistributable"></a>Çalışma zamanını yeniden dağıtılabilir kullanarak yükler

 çalışma zamanını, Office çalışma zamanının el ile yeniden dağıtılabilir Visual Studio 2010 araçlarını çalıştırarak veya bir Office çözümü dağıtırken yeniden dağıtılabilir bir önkoşul olarak ekleyerek yükleyebilirsiniz.

 çalışma zamanını, Office çalışma zamanı yeniden dağıtılabilir için Visual Studio 2010 araçlarını kullanarak yüklediğinizde, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] Office ilgili sürümleri bilgisayarda zaten mevcutsa, .NET Framework 3,5 için Office uzantıları ve .NET Framework uzantıları yüklenir. çalışma zamanı yüklenirken bilgisayarda bu .NET Framework sürümlerinden biri eksikse, .NET Framework eksik sürümü için Office uzantıları o anda yüklenmez. .NET Framework eksik sürümünü daha sonra yüklerseniz, uzantıları gerektiren bir çözümün yüklenmesi (çalışma zamanı ClickOnce kullanılarak dağıtılan bir çözümle birlikte yüklendiyse) veya yüklenilişinde (çalışma zamanı Windows Installer kullanılarak dağıtılan bir çözümle yüklenmişse), ilgili Office uzantıları otomatik olarak yüklenir.

 ClickOnce çözümüne önkoşulları ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: son kullanıcı bilgisayarlarına önkoşulları yüklemek Office çözümleri çalıştırma](/previous-versions/bb608608(v=vs.110)). yeniden dağıtılabilir paketten çalışma zamanının el ile nasıl yükleneceği hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office için Visual Studio Araçları çalışma zamanı yeniden dağıtılabilir](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Office için Visual Studio Araçları çalışma zamanına genel bakış](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Office için Visual Studio Araçları çalışma zamanında derlemeler](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
