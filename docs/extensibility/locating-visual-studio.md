---
title: Konum Visual Studio | Microsoft Docs
description: Aynı sürümde birden çok örnek yükleyebilirsiniz Visual Studio. Com sorgu API'sini kullanarak istediğiniz örneği bulma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
author: leslierichardson95
ms.author: lerich
ms.workload:
- vssdk
ms.openlocfilehash: cd0fcd294983d6a6567676f06703b4bd1dd376c4
ms.sourcegitcommit: b4cc3dee59421f7089112becf128a369acadaf61
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2021
ms.locfileid: "112990512"
---
# <a name="locate-visual-studio"></a>Visual Studio’yu Bulma

2017'Visual Studio başlayarak, aynı sürümün veya hatta sürümün birden çok örneğini yükleyebilirsiniz. Bu, önceki yüklemenizi yaparken birincil geliştirme makinenize yeni işlevlerin önizlemesini görüntülemek istediğiniz zaman yararlıdır. Bu değişiklikler nedeniyle bir örneği bulmak için kullanabileceğiniz tek bir ortam değişkeni veya kayıt defteri değeri yoktur. Bunun yerine, uzantınıza uygun [ölçütlere](/dotnet/api/microsoft.visualstudio.setup.configuration) göre örnekleri bulmak için bir COM sorgu API'si kullanabilirsiniz.

Bu, yerel ve yönetilen kod için kullanılabilen NuGet paketlerine sahip hızlı ve salt okunur bir API'dir.

| Kod | Paket |
| ---- | --- |
| Yerel | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Yönetilen | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Bir yol veya geçerli işlem verilen tek bir örneği bulup tüm örnekleri numaralara saldırarak. Veri [örneklerinin yerinin](https://github.com/Microsoft/vs-setup-samples) nasıl bulunarak ilgili tüm örnekler için Visual Studio.

## <a name="tools"></a>Araçlar

Derleme Visual Studio, PowerShell betikleri, yükleyiciler ve daha fazla senaryodaki diğer araçları ve diğer araçları bulmak için, doğrudan kullanabileceğiniz veya kendi betiklerinizi yeniden dağıtabilirsiniz bir dizi açık kaynak araç vardır.

| Proje | Açıklama |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Yayın veya yayın öncesi, hangi ürünün yüklü olduğu ve hangi iş yüklerinin yüklü olduğu gibi ölçütlere uyan örnekleri bulmak için tek dosyalı yerel yürütülebilir dosya. Ayrıca 2010 ve Visual Studio için daha az bilgi döndürülse de 2017 ve Visual Studio bulma desteği de verilir. Örnekler için [wiki'ye](https://github.com/Microsoft/vswhere/wiki) bakın. |
| [VSSetup cmdlet'leri](https://github.com/Microsoft/vssetup.powershell) | PowerShell cmdlet'leri, 2.0 ve daha yeni sürümleri destekler. Bu cmdlet'ler, _vswhere_ ile aynı ölçütlere göre örnekleri bulmak ve örnekler hakkında daha da fazla özellik bulmak için kullanabileceğiniz nesneler olarak zengin bilgiler sağlar. Örnekler için [wiki'ye](https://github.com/Microsoft/vssetup.powershell/wiki) bakın. |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | _VSIXInstaller'ı otomatik_ olarak bulup bir **.vsix* dosyası yüklemek için komut satırına geçer. Bu özellik, sorgu API'leri için doğrudan desteği olan yükleyicilerde yararlı olabilir. Örnekler için [wiki'ye](https://github.com/Microsoft/vsixbootstrapper/wiki) bakın. |

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 2017 kurulumunda yapılan değişiklikler](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
* [DTE kullanarak Visual Studio’yu Başlatma](launch-visual-studio-dte.md)
