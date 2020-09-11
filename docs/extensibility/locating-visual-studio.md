---
title: Visual Studio 'Yu bulma | Microsoft Docs
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 93a6f39a9240002cd8008c9368799e10ab63b78d
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012483"
---
# <a name="locate-visual-studio"></a>Visual Studio’yu Bulma

Visual Studio 2017 ' den itibaren, aynı sürümden veya hatta sürümden daha fazla örnek yükleyebilirsiniz. Bu, önceki yüklemenizi korurken birincil geliştirme makinenizdeki yeni işlevselliği önizlemek istediğinizde yararlıdır. Bu değişiklikler nedeniyle, bir örneği bulmak için kullanabileceğiniz tek bir ortam değişkeni veya kayıt defteri değeri yoktur. Bunun yerine, uzantınızla ilgili ölçütlere göre örnekleri bulmak için bir [com sorgu API 'si](/dotnet/api/microsoft.visualstudio.setup.configuration) kullanabilirsiniz.

Bu, yerel ve yönetilen kod için kullanılabilen NuGet paketlerine sahip hızlı, salt okunurdur bir API 'dir.

| Kod | Paket |
| ---- | --- |
| Yerel | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Yönetilen | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Bir yol veya geçerli işlem verilen tek bir örneği bulabilir veya tüm örnekleri numaralandırabilirsiniz. Visual Studio 'Yu nasıl bulaöğreneceksiniz hakkında tüm [örneklere bakın.](https://github.com/Microsoft/vs-setup-samples)

## <a name="tools"></a>Araçlar

Visual Studio 'Yu ve derleme ortamlarında, PowerShell betikleri, yükleyicilerinin ve diğer senaryolarda bulunan diğer araçları bulmak için, doğrudan veya kendi betiklerinizde birlikte kullanabileceğiniz bir dizi açık kaynak aracı vardır.

| Proje | Açıklama |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Yayın veya ön sürüm, hangi ürünün yüklendiği ve hangi iş yüklerinin yüklendiği gibi toplantı ölçütlerini bulmak için tek dosya yerel yürütülebilir dosyası. Visual Studio 2010 ve üstünü bulmayı da destekler, ancak Visual Studio 2017 ve daha yeni bir sürümü daha az bilgi döndürülür. Örnekler için bkz. [wiki](https://github.com/Microsoft/vswhere/wiki) . |
| [VSSetup cmdlet 'leri](https://github.com/Microsoft/vssetup.powershell) | PowerShell cmdlet 'leri, benzer ölçütlere göre örnekleri bulmak ve örnekler hakkında daha fazla özelliği bulmak için kullanabileceğiniz bir _nesne olarak zengin_ bilgileri döndüren 2,0 ve daha yeni bir sürümü destekler. Örnekler için bkz. [wiki](https://github.com/Microsoft/vssetup.powershell/wiki) . |
| [Valtıönyükleyici](https://github.com/Microsoft/vsixbootstrapper) | _Valtıyükleyici_ 'yi otomatik olarak bulur ve bir **. vsix* dosyası yüklemek için komut satırını aracılığıyla geçirir. Bu özellik sorgu API 'Leri için doğrudan desteğe sahip olmayan yükleyicilerle yararlı olabilir. Örnekler için bkz. [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) . |

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 2017 kurulumu değişiklikleri](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
* [DTE kullanarak Visual Studio’yu Başlatma](launch-visual-studio-dte.md)