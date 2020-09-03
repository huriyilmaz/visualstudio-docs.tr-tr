---
title: Ürün anahtarlarını otomatik olarak Uygula
description: Visual Studio 'Yu dağıtırken ürün anahtarlarını programlama yoluyla nasıl uygulayacağınızı öğrenin.
ms.date: 09/24/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e7f331536de264186bc2977cc4acaaab02147e13
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76115223"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Visual Studio’yu dağıtırken ürün anahtarlarını otomatik olarak uygulama

Ürün anahtarınızı, Visual Studio 'nun dağıtımını otomatik hale getirmek için kullanılan bir betiğin parçası olarak programlı bir şekilde uygulayabilirsiniz. Bir Visual Studio yüklemesi sırasında veya bir yükleme tamamlandıktan sonra, bir cihazda bir ürün anahtarı programlama yoluyla ayarlayabilirsiniz.

## <a name="apply-the-license-after-installation"></a>Yüklemeden sonra lisansı Uygula

::: moniker range="vs-2017"

Visual Studio 'nun yüklü bir sürümünü `StorePID.exe` , hedef makinelerdeki yardımcı programını sessiz modda kullanarak bir ürün anahtarıyla etkinleştirebilirsiniz. `StorePID.exe` , aşağıdaki varsayılan konumda Visual Studio 2017 ile yüklenen bir yardımcı programdır: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 'nun yüklü bir sürümünü `StorePID.exe` , hedef makinelerdeki yardımcı programını sessiz modda kullanarak bir ürün anahtarıyla etkinleştirebilirsiniz. `StorePID.exe` , aşağıdaki varsayılan konumda Visual Studio 2019 ile yüklenen bir yardımcı programdır: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE`

::: moniker-end

 `StorePID.exe`Bir System Center Aracısı ya da yükseltilmiş bir komut istemi kullanarak yükseltilmiş ayrıcalıklarla çalıştırın. Ürün anahtarı ve Microsoft ürün kodu (MPC) ile birlikte izleyin.

>[!IMPORTANT]
> Ana çizgileri ürün anahtarına eklediğinizden emin olun.

 ```cmd
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker range="vs-2017"

Aşağıdaki örnek, MPC/08860, ürün anahtarı `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` ve varsayılan yükleme konumunu varsayan Visual Studio 2017 Enterprise lisansını uygulamak için bir komut satırı gösterir:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
```

::: moniker-end

::: moniker range="vs-2019"

Aşağıdaki örnek, MPC/09260, ürün anahtarı `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` ve varsayılan yükleme konumunu varsayan Visual Studio 2019 Enterprise lisansını uygulamak için bir komut satırı gösterir:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 09260
```

::: moniker-end

::: moniker range="vs-2017"

 Aşağıdaki tabloda, Visual Studio 'nun her sürümü için MPC kodları listelenmektedir:

| Visual Studio sürümü                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Uzmanı 2017 | 08866 |

::: moniker-end

::: moniker range="vs-2019"

| Visual Studio sürümü                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2019        | 09260 |
| Visual Studio Professional 2019      | 09262 |

::: moniker-end

`StorePID.exe`Ürün anahtarı başarıyla geçerliyse, 0 değerini döndürür `%ERRORLEVEL%` . Hatalarla karşılaşırsa, hata koşuluna bağlı olarak aşağıdaki kodlardan birini döndürür:

| Hata                     | Kod |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

> [!NOTE]
> Visual Studio 'nun bir sanal örneğini çalıştırdığınızda, Yerel AppData klasörünü ve kayıt defterini de sanallaştırdığınızdan emin olun. Sanal örneklerin sorunlarını gidermek için, öğesini çalıştırın `C:\Program Files (x86)\Microsoft Visual Studio\<version>\Common7\IDE\DDConfigCA.exe` .  

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](../install/install-visual-studio.md)
* [Visual Studio’nun çevrimdışı yüklemesini oluşturma](../install/create-an-offline-installation-of-visual-studio.md)
