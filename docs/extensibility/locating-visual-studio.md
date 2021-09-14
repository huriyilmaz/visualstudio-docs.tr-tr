---
title: Visual Studio bulunuyor | Microsoft Docs
description: Aynı Visual Studio sürümünün birden fazla örneğini yükleyebilirsiniz. İstediğiniz örneği bulmak için bir COM sorgu API 'sini nasıl kullanacağınızı öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724974"
---
# <a name="locate-visual-studio"></a>Visual Studio’yu Bulma

Visual Studio 2017 ' den başlayarak aynı sürümün veya hatta sürümünün birden çok örneğini yükleyebilirsiniz. Bu, önceki yüklemenizi korurken birincil geliştirme makinenizdeki yeni işlevselliği önizlemek istediğinizde yararlıdır. Bu değişiklikler nedeniyle, bir örneği bulmak için kullanabileceğiniz tek bir ortam değişkeni veya kayıt defteri değeri yoktur. Bunun yerine, uzantınızla ilgili ölçütlere göre örnekleri bulmak için bir [com sorgu API 'si](/dotnet/api/microsoft.visualstudio.setup.configuration) kullanabilirsiniz.

bu, yerel ve yönetilen kod için kullanılabilir NuGet paketlerine sahip hızlı, salt okunurdur bir apı 'dir.

| Kod | Paket |
| ---- | --- |
| Yerel | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Yönetilen | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Bir yol veya geçerli işlem verilen tek bir örneği bulabilir veya tüm örnekleri numaralandırabilirsiniz. Visual Studio nasıl bulunacağını gösteren tüm örneklere yönelik [örneklerimize](https://github.com/Microsoft/vs-setup-samples) bakın.

## <a name="tools"></a>Araçlar

yapı ortamları, PowerShell betikleri, yükleyiciler ve daha fazla senaryoda Visual Studio ve diğer araçları bulmak için, doğrudan kullanabileceğiniz veya kendi betikleriyle birlikte kullanabileceğiniz bir dizi açık kaynak aracı vardır.

| Proje | Açıklama |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Yayın veya ön sürüm, hangi ürünün yüklendiği ve hangi iş yüklerinin yüklendiği gibi toplantı ölçütlerini bulmak için tek dosya yerel yürütülebilir dosyası. ayrıca, Visual Studio 2017 ve daha yeni bir için Visual Studio 2010 ve üstünü bulmayı da destekler. Örnekler için bkz. [wiki](https://github.com/Microsoft/vswhere/wiki) . |
| [VSSetup cmdlet 'leri](https://github.com/Microsoft/vssetup.powershell) | PowerShell cmdlet 'leri, benzer ölçütlere göre örnekleri bulmak ve örnekler hakkında daha fazla özelliği bulmak için kullanabileceğiniz bir _nesne olarak zengin_ bilgileri döndüren 2,0 ve daha yeni bir sürümü destekler. Örnekler için bkz. [wiki](https://github.com/Microsoft/vssetup.powershell/wiki) . |
| [Valtıönyükleyici](https://github.com/Microsoft/vsixbootstrapper) | _Valtıyükleyici_ 'yi otomatik olarak bulur ve bir **. vsix* dosyası yüklemek için komut satırını aracılığıyla geçirir. Bu özellik sorgu API 'Leri için doğrudan desteğe sahip olmayan yükleyicilerle yararlı olabilir. Örnekler için bkz. [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) . |

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 2017 kurulumu değişiklikleri](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
* [DTE kullanarak Visual Studio’yu Başlatma](launch-visual-studio-dte.md)
