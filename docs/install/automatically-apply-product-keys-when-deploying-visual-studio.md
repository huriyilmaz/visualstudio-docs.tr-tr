---
title: Ürün anahtarlarını otomatik olarak Uygula
description: Visual Studio dağıtırken ürün anahtarlarını programlama yoluyla nasıl uygulayacağınızı öğrenin.
ms.date: 09/24/2019
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3f3930744ad99f301660ddb8e395fa61f4ea79fd
ms.sourcegitcommit: 215680b355cf613bfa125cf6b864c8bb5f2c71a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2021
ms.locfileid: "132453431"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Visual Studio’yu dağıtırken ürün anahtarlarını otomatik olarak uygulama

Visual Studio dağıtımını otomatik hale getirmek için kullanılan bir betiğin parçası olarak ürün anahtarınızı programlı bir şekilde uygulayabilirsiniz. bir Visual Studio yüklemesi sırasında veya bir yükleme tamamlandıktan sonra, bir cihazda bir ürün anahtarı programlama yoluyla ayarlayabilirsiniz.

::: moniker range=">=vs-2022"

> [!IMPORTANT]
> Visual Studio 2022 şu anda önizlemededir ve önizleme dönemi boyunca 2022 Visual Studio ürün anahtarının uygulanmasını gerektirmeyen bir değerlendirme lisansında kullanılabilir.

::: moniker-end

::: moniker range="vs-2017"

## <a name="apply-the-license-after-installation"></a>Yüklemeden sonra lisansı Uygula

bir Visual Studio yüklü sürümünü `StorePID.exe` , hedef makinelerdeki yardımcı programını sessiz modda kullanarak bir ürün anahtarıyla etkinleştirebilirsiniz. `StorePID.exe`, aşağıdaki varsayılan konumda Visual Studio 2017 ile yüklenen bir yardımcı programdır:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE
```

 `StorePID.exe`System Center aracısı veya yükseltilmiş bir komut istemi kullanarak yükseltilmiş ayrıcalıklarla çalıştırın. Ürün anahtarı ve Microsoft ürün kodu (MPC) ile birlikte izleyin.

>[!IMPORTANT]
> Ana çizgileri ürün anahtarına eklediğinizden emin olun.

 ```shell
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker-end

::: moniker range="vs-2019"

## <a name="apply-the-license-after-installation"></a>Yüklemeden sonra lisansı Uygula

bir Visual Studio yüklü sürümünü `StorePID.exe` , hedef makinelerdeki yardımcı programını sessiz modda kullanarak bir ürün anahtarıyla etkinleştirebilirsiniz. `StorePID.exe`, aşağıdaki varsayılan konumda Visual Studio 2019 ile yüklenen bir yardımcı programdır:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE
```

 `StorePID.exe`System Center aracısı veya yükseltilmiş bir komut istemi kullanarak yükseltilmiş ayrıcalıklarla çalıştırın. Ürün anahtarı ve Microsoft ürün kodu (MPC) ile birlikte izleyin.

>[!IMPORTANT]
> Ana çizgileri ürün anahtarına eklediğinizden emin olun.

 ```shell
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker-end

::: moniker range="vs-2017"

aşağıdaki örnek, mpc/08860, ürün anahtarı `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` ve varsayılan yükleme konumunu varsayan Visual Studio 2017 Enterprise için lisans uygulamak için bir komut satırı gösterir:

```shell
"C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
```

::: moniker-end

::: moniker range="vs-2019"

aşağıdaki örnek, mpc/09260, ürün anahtarı `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` ve varsayılan yükleme konumunu varsayan Visual Studio 2019 Enterprise için lisans uygulamak için bir komut satırı gösterir:

```shell
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 09260
```

::: moniker-end

::: moniker range="vs-2017"

 Aşağıdaki tabloda her bir Visual Studio sürümü için MPC kodları listelenmektedir:

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

::: moniker range="vs-2017"

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
> bir Visual Studio sanal örneğini çalıştırdığınızda, yerel AppData klasörünü ve kayıt defterini de sanallaştırdığınızdan emin olun. Sanal örneklerin sorunlarını gidermek için, öğesini çalıştırın `<Visual Studio installation directory>\Common7\IDE\DDConfigCA.exe` .  

::: moniker-end

::: moniker range="vs-2019"

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
> bir Visual Studio sanal örneğini çalıştırdığınızda, yerel AppData klasörünü ve kayıt defterini de sanallaştırdığınızdan emin olun. Sanal örneklerin sorunlarını gidermek için, öğesini çalıştırın `<Visual Studio installation directory>\Common7\IDE\DDConfigCA.exe` .  

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](../install/install-visual-studio.md)
* [Visual Studio’nun çevrimdışı yüklemesini oluşturma](../install/create-an-offline-installation-of-visual-studio.md)