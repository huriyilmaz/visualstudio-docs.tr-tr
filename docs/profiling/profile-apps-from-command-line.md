---
title: Komut satırından performans ölçme
description: Komut satırından uygulamanızdaki CPU performansını ve yönetilen bellek kullanımını ölçün.
ms.custom: ''
ms.date: 02/21/2020
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, command-line
- Diagnostics Tools, command-line
- CPU Usage, command-line
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 0b1d5906213b148605e35c483b377280dc942515
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936554"
---
# <a name="measure-application-performance-from-the-command-line"></a>Komut satırından uygulama performansını ölçme

Komut satırı araçlarını kullanarak bir uygulamayla ilgili performans bilgilerini toplayabilirsiniz.

Bu makalede açıklanan örnekte, Microsoft Notepad için performans bilgilerini topladığınızda, ancak aynı yöntem herhangi bir işlemi profilde de kullanılabilir.

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio 2019 veya sonraki sürümleri

* Komut satırı araçlarıyla benzerlik

* Visual Studio yüklü olmayan bir uzak makinede performans bilgilerini toplamak için [Visual Studio için uzak Araçlar](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019) uzak makineye yükleme. Araçların sürümü Visual Studio sürümünüz ile aynı olmalıdır.

## <a name="collect-performance-data"></a>Performans verilerini topla

Visual Studio tanılama CLı araçları kullanılarak profil oluşturma işlemi, toplayıcı aracılarından biri ile birlikte profil oluşturma aracını bir işleme ekleyerek işe yarar. Profil oluşturma aracını eklediğinizde, araç durduruluncaya kadar profil oluşturma verilerini yakalayan ve depolayan bir tanılama oturumuna başlarsınız ve bu, verilerin bir *. diagsession* dosyasına aktarılmasıdır. Ardından, sonuçları çözümlemek için bu dosyayı Visual Studio 'da açabilirsiniz.

1. Not defteri 'ni başlatın ve sonra işlem KIMLIĞINI (PID) almak için Görev Yöneticisi 'Ni açın. Görev Yöneticisi 'nde, **Ayrıntılar** sekmesinde PID 'yi bulun.

1. Bir komut istemi açın ve genellikle burada (Visual Studio Enterprise için) koleksiyon Aracısı yürütülebiliri ile dizinde geçiş yapın.

   ```<Visual Studio installation folder>\2019\Enterprise\Team Tools\DiagnosticsHub\Collector\```

1. Aşağıdaki komutu yazarak *VSDiagnostics.exe* başlatın.

   ```cmd
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   Dahil olması gereken bağımsız değişkenler şunlardır:

   * \<*id*> Koleksiyon oturumunu tanımlar. KIMLIK 1-255 arasında bir sayı olmalıdır.
   * \<*pid*>, Bu durumda, profil atamak istediğiniz işlemin PID 'si, 1. adımda bulduğunuz PID.
   * \<*configFile*>, başlatmak istediğiniz koleksiyon aracısının yapılandırma dosyası. Daha fazla bilgi için bkz. [aracılar Için yapılandırma dosyaları](#config_file).

   Örneğin, daha önce açıklandığı gibi, *PID* 'Yi değiştirerek CPUUsageBase Aracısı için aşağıdaki komutu kullanabilirsiniz.

   ```cmd
   VSDiagnostics.exe start 1 /attach:<pid> /loadConfig:AgentConfigs\CPUUsageLow.json
   ```

1. Not defteri 'ni yeniden boyutlandırın veya bazı ilgi çekici profil bilgilerinin toplandığından emin olmak için buna bir şey yazın.

1. Aşağıdaki komutu yazarak koleksiyon oturumunu durdurun ve çıktıyı bir dosyaya gönderin.

   ```cmd
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

1. Önceki komuttan *. diagsession* dosyası çıkışını bulun ve toplanan bilgileri incelemek için Visual Studio (**Dosya**  >  **Aç**) içinde açın.

   Sonuçları çözümlemek için, ilgili performans aracına yönelik belgelere bakın. Örneğin, bu [CPU kullanımı](../profiling/cpu-usage.md), [.NET nesne ayırma aracı](../profiling/dotnet-alloc-tool.md)veya [veritabanı](../profiling/analyze-database.md) aracı olabilir.

## <a name="agent-configuration-files"></a><a name="config_file"></a> Aracı yapılandırma dosyaları

Koleksiyon aracıları, ölçmeye çalıştığınız seçeneğe bağlı olarak farklı veri türlerini toplamanızı sağlayan, değiştirilebilir bileşenlerdir.

Kolaylık olması için, bu bilgileri bir aracı yapılandırma dosyasında saklayabilirsiniz. Yapılandırma dosyası, en az *. dll* ve com CLSID adını içeren bir *. JSON* dosyasıdır. Aşağıdaki klasörde bulabileceğiniz örnek yapılandırma dosyaları aşağıda verilmiştir:

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

CpuUsage yapılandırması (taban/yüksek/düşük), [CPU kullanımı](../profiling/cpu-usage.md) profil oluşturma aracı için toplanan verilere karşılık gelir.
DotNetObjectAlloc yapılandırması (taban/düşük), [.NET nesne ayırma aracı](../profiling/dotnet-alloc-tool.md)için toplanan verilere karşılık gelir.

Taban/düşük/yüksek yapılandırma örnekleme hızına başvurur. Örneğin, düşük değer 100 örnek/saniye ve yüksek 4000 örnek/saniye.

*VSDiagnostics.exe* aracının bir koleksiyon aracısıyla çalışması için, uygun aracı IÇIN hem dll hem de com CLSID gerektirir ve aracının ek yapılandırma seçenekleri de olabilir. Yapılandırma dosyası olmadan bir aracı kullanıyorsanız, aşağıdaki komutta biçimini kullanın.

```cmd
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```

## <a name="permissions"></a>İzinler

Yükseltilmiş izinler gerektiren bir uygulamayı profil oluşturma için, bunu yükseltilmiş bir komut isteminden yapmanız gerekir.
