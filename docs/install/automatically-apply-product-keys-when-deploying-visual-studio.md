---
title: Ürün anahtarlarını otomatik olarak uygulama
description: Ürün anahtarlarını program aracılığıyla uygulama hakkında bilgi edinmek için Visual Studio.
ms.date: 09/24/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: a78da89d8e8ce4251bc9288270628bfe784eca7a
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307728"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Visual Studio’yu dağıtırken ürün anahtarlarını otomatik olarak uygulama

Ürün anahtarınızı program aracılığıyla, uygulama dağıtımını otomatikleştirmek için kullanılan bir betiğin parçası olarak Visual Studio. Ürün anahtarını, cihaz yüklemesi sırasında veya yükleme tamamlandıktan Visual Studio bir cihaza program aracılığıyla kurabilirsiniz.

::: moniker range=">=vs-2022"

> [!IMPORTANT]
> Visual Studio 2022 şu anda önizlemededir ve önizleme döneminde Visual Studio 2022, ürün anahtarının uygulanmasına gerek gerektirmeyen bir değerlendirme lisansı altında kullanılabilir.

::: moniker-end

::: moniker range="vs-2017"

## <a name="apply-the-license-after-installation"></a>Yüklemeden sonra lisansı uygulama

Hedef makinelerde yardımcı programını kullanarak Visual Studio bir ürün anahtarıyla yüklü bir sürümü `StorePID.exe` sessiz modda etkinleştirebilirsiniz. `StorePID.exe` , aşağıdaki varsayılan konumda Visual Studio 2017 ile yükleyen bir yardımcı programdır:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE
```

 Bir System Center aracı veya yükseltilmiş komut `StorePID.exe` istemi kullanarak yükseltilmiş ayrıcalıklarla çalıştırın. Ürün anahtarı ve Microsoft Ürün Kodu (MPC) ile bunu izleyin.

>[!IMPORTANT]
> Tireleri ürün anahtarına dahil etmek için emin olun.

 ```shell
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker-end

::: moniker range="vs-2019"

## <a name="apply-the-license-after-installation"></a>Yüklemeden sonra lisansı uygulama

Hedef makinelerde yardımcı programını kullanarak Visual Studio bir ürün anahtarıyla yüklü bir sürümü `StorePID.exe` sessiz modda etkinleştirebilirsiniz. `StorePID.exe` , aşağıdaki varsayılan konumda Visual Studio 2019 ile yükleyen bir yardımcı programdır:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE
```

 Bir System Center aracı veya yükseltilmiş komut `StorePID.exe` istemi kullanarak yükseltilmiş ayrıcalıklarla çalıştırın. Ürün anahtarı ve Microsoft Ürün Kodu (MPC) ile bunu izleyin.

>[!IMPORTANT]
> Tireleri ürün anahtarına dahil etmek için emin olun.

 ```shell
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker-end

::: moniker range="vs-2017"

Aşağıdaki örnekte, MPC değeri 08860 olan ve varsayılan yükleme konumu varsayan Visual Studio 2017 Enterprise lisansının uygulanması için bir komut satırı `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` gösterir:

```shell
"C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
```

::: moniker-end

::: moniker range="vs-2019"

Aşağıdaki örnekte, MPC değeri 09260 olan ve varsayılan yükleme konumu varsayan Visual Studio 2019 Enterprise lisansının uygulanması için bir komut satırı `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` gösterir:

```shell
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 09260
```

::: moniker-end

::: moniker range="vs-2017"

 Aşağıdaki tabloda, her bir sürüm için MPC kodları Visual Studio:

| Visual Studio Edition                | Mpc   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Uzmanı 2017 | 08866 |

::: moniker-end

::: moniker range="vs-2019"

| Visual Studio Edition                | Mpc   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2019        | 09260 |
| Visual Studio Professional 2019      | 09262 |

::: moniker-end

::: moniker range="vs-2017"

Ürün `StorePID.exe` anahtarını başarıyla uygularsa, `%ERRORLEVEL%` 0 döndürür. Hatalarla karşılaşırsa, hata koşuluna bağlı olarak aşağıdaki kodlardan birini döndürür:

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
> Sanal bir uygulama örneği Visual Studio, yerel AppData klasörünü ve kayıt defterini de sanallaştırabilirsiniz. Sanal örneklerde sorun gidermek için `<Visual Studio installation directory>\Common7\IDE\DDConfigCA.exe` çalıştırın.  

::: moniker-end

::: moniker range="vs-2019"

Ürün `StorePID.exe` anahtarını başarıyla uygularsa, `%ERRORLEVEL%` 0 döndürür. Hatalarla karşılaşırsa, hata koşuluna bağlı olarak aşağıdaki kodlardan birini döndürür:

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
> Sanal bir uygulama örneği Visual Studio, yerel AppData klasörünü ve kayıt defterini de sanallaştırabilirsiniz. Sanal örneklerde sorun gidermek için `<Visual Studio installation directory>\Common7\IDE\DDConfigCA.exe` çalıştırın.  

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](../install/install-visual-studio.md)
* [Visual Studio’nun çevrimdışı yüklemesini oluşturma](../install/create-an-offline-installation-of-visual-studio.md)