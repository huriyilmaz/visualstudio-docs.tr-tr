---
title: Komut satırından performans ölçme
description: Komut satırıyla uygulamanıza CPU performansını ve yönetilen bellek kullanımını ölçün.
ms.custom: ''
ms.date: 09/13/2021
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, command-line
- Diagnostics Tools, command-line
- CPU Usage, command-line
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 5ebc503d8b1733968b94f09256b139b84296c708
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128428717"
---
# <a name="measure-application-performance-from-the-command-line"></a>Komut satırıyla uygulama performansını ölçme

Komut satırı araçlarını kullanarak bir uygulama hakkında performans bilgileri toplayabilirsiniz.

Bu makalede açıklanan örnekte, Microsoft Not Defteri için performans bilgilerini toplayabilirsiniz, ancak herhangi bir işlem profili oluşturmak için aynı yöntem kullanılabilir.

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio 2019 veya sonraki sürümler

* Komut satırı araçları hakkında bilgi

* Yüklü olmayan bir uzak makinede performans bilgilerini Visual Studio için uzak [makineye Visual Studio için Uzak Araçlar](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019) yükleyin. Araçların sürümü, Visual Studio.

## <a name="collect-performance-data"></a>Performans verilerini toplama

Visual Studio Tanılama CLI araçlarını kullanarak profil oluşturma işlemi, profil oluşturma aracını toplayıcı aracılarından biri ile birlikte bir işleme iliştirerek çalışır. Profil oluşturma aracını iliştirerek, profil oluşturma verilerini yakalayan ve araç durdurulana kadar depolayan bir tanılama oturumu başlar ve bu noktada veriler *bir .diagsession* dosyasına dışarı aktarılıyor. Ardından sonuçları analiz etmek için bu Visual Studio içinde açabilirsiniz.

1. Görev Not Defteri'ı ve ardından işlem kimliğini (PID) almak için Görev Yöneticisi'ni açın. Görev Yöneticisi'nde, Ayrıntılar sekmesinde **PID'i** bulun.

1. Bir komut istemi açın ve genellikle burada (örneğin, koleksiyon aracısı yürütülebilir dosyası) dizinine Visual Studio Enterprise.

   ::: moniker range=">= vs-2022"
   ```<Visual Studio installation folder>\2022\Enterprise\Team Tools\DiagnosticsHub\Collector\```
   ::: moniker-end
   ::: moniker range="vs-2019"
   ```<Visual Studio installation folder>\2019\Enterprise\Team Tools\DiagnosticsHub\Collector\```
   ::: moniker-end

1. Aşağıdaki *VSDiagnostics.exe* yazarak başlangıç yapın.

   ```cmd
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   Dahil edilecek bağımsız değişkenler:

   * \<*id*> Koleksiyon oturumunu tanımlar. Kimlik, 1-255 arasında bir sayı olabilir.
   * \<*pid*>, profilini oluşturmak istediğiniz sürecin PID'i, bu durumda 1. adımda bulunan PID.
   * \<*configFile*>, başlatmak istediğiniz koleksiyon aracısı için yapılandırma dosyası. Daha fazla bilgi için [bkz. Aracılar için yapılandırma dosyaları.](#config_file)

   Örneğin, daha önce açıklandığı gibi *pid'i* değiştirerek CPUUsageBase aracısı için aşağıdaki komutu kullanabilirsiniz.

   ```cmd
   VSDiagnostics.exe start 1 /attach:<pid> /loadConfig:AgentConfigs\CPUUsageLow.json
   ```

1. Bazı Not Defteri bilgileri toplanmış olduğundan emin olmak için yeniden boyutlandırabilir veya bir şeyler yazabilirsiniz.

1. Aşağıdaki komutu yazarak koleksiyon oturumunu durdurun ve çıktıyı bir dosyaya gönderin.

   ```cmd
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

1. Önceki *komuttan .diagsession* dosyası çıktısını bulun ve toplanan bilgileri incelemek için Visual Studio **(** Dosya  >  **Aç**) içinde açın.

   Sonuçları analiz etmek için ilgili performans aracının belgelerine bakın. Örneğin, bu [CPU](../profiling/cpu-usage.md)Kullanımı , [.NET Nesne Ayırma aracı](../profiling/dotnet-alloc-tool.md)veya Veritabanı [aracı](../profiling/analyze-database.md) olabilir.

## <a name="agent-configuration-files"></a><a name="config_file"></a> Aracı yapılandırma dosyaları

Toplama Aracıları, neyi ölçmeye çalıştığınıza bağlı olarak farklı veri türlerini toplayan değiştirilebilir bileşenlerdir.

Kolaylık olması için bu bilgileri bir aracı yapılandırma dosyasında depolamanız önerilir. Yapılandırma dosyası, en azından dosyanın adını ve COM CLSID'sini *.dll* *bir .json* dosyasıdır. Aşağıdaki klasörde aşağıdaki örnek yapılandırma dosyalarını bulabilirsiniz:

```<Visual Studio installation folder>Team Tools\DiagnosticsHub\Collector\AgentConfigs\```

Aracı yapılandırma dosyalarını indirmek ve görüntülemek için lütfen aşağıdaki bağlantılara bakın:

- https://aka.ms/vs/diaghub/agentconfig/cpubase
- https://aka.ms/vs/diaghub/agentconfig/cpuhigh
- https://aka.ms/vs/diaghub/agentconfig/cpulow
- https://aka.ms/vs/diaghub/agentconfig/database
- https://aka.ms/vs/diaghub/agentconfig/dotnetasyncbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetallocbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetalloclow
- https://aka.ms/vs/diaghub/agentconfig/dotnetcountersbase

CpuUsage yapılandırmaları (Temel/Yüksek/Düşük), CPU Kullanımı profil [oluşturma aracı için toplanan verilere](../profiling/cpu-usage.md) karşılık gelir.
DotNetObjectAlloc yapılandırmaları (Temel/Düşük), .NET Nesne Ayırma aracı [için toplanan verilere karşılık gelir.](../profiling/dotnet-alloc-tool.md)

Temel/Düşük/Yüksek yapılandırmalar örnekleme oranına başvurur. Örneğin, Düşük 100 örnek/saniye, Yüksek ise 4000 örnek/saniyedir.

Bir *VSDiagnostics.exe* aracının bir koleksiyon aracısı ile çalışması için, uygun aracı için hem DLL hem de COM CLSID gerekir. Aracının ek yapılandırma seçenekleri de olabilir. Bu, yapılandırma dosyasında belirtilen ve düzgün bir şekilde kaçarak JSON olarak biçimlendirilmiş seçenekler olabilir.

## <a name="permissions"></a>İzinler

Yükseltilmiş izinler gerektiren bir uygulamanın profilini oluşturmak için, bunu yükseltilmiş bir komut isteminden yapmak gerekir.
