---
title: Ürün anahtarlarını otomatik olarak uygulayın
description: Visual Studio'yı dağıtırken ürün anahtarlarını programlı olarak nasıl uygulayacağınızı öğrenin.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115223"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Visual Studio’yu dağıtırken ürün anahtarlarını otomatik olarak uygulama

Ürün anahtarınızı Visual Studio'nun dağıtımını otomatikleştirmek için kullanılan bir komut dosyasının parçası olarak programlı olarak uygulayabilirsiniz. Visual Studio yüklemesi sırasında veya yükleme tamamlandıktan sonra bir aygıtüzerinde programlı olarak bir ürün anahtarı ayarlayabilirsiniz.

## <a name="apply-the-license-after-installation"></a>Yüklemeden sonra lisansı uygulayın

::: moniker range="vs-2017"

Visual Studio'nun yüklü bir sürümünü, hedef makinelerdeki `StorePID.exe` yardımcı programı sessiz modda kullanarak ürün anahtarıyla etkinleştirebilirsiniz. `StorePID.exe`Visual Studio 2017 ile aşağıdaki varsayılan konuma yüklenen bir yardımcı programdır: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

::: moniker-end

::: moniker range="vs-2019"

Visual Studio'nun yüklü bir sürümünü, hedef makinelerdeki `StorePID.exe` yardımcı programı sessiz modda kullanarak ürün anahtarıyla etkinleştirebilirsiniz. `StorePID.exe`Visual Studio 2019 ile aşağıdaki varsayılan konumda yüklenen bir yardımcı programdır: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE`

::: moniker-end

 Bir `StorePID.exe` System Center aracısı veya yükseltilmiş komut istemi kullanarak yüksek ayrıcalıklarla çalıştırın. Ürün anahtarı ve Microsoft Ürün Kodu (MPC) ile izleyin.

>[!IMPORTANT]
> Tireleri ürün anahtarına eklediğinden emin olun.

 ```cmd
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker range="vs-2017"

Aşağıdaki örnekte, 08860 mpc'si olan ve varsayılan yükleme konumunu varsayan Visual Studio 2017 Enterprise lisansıiçin `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`bir komut satırı gösterilmektedir:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
```

::: moniker-end

::: moniker range="vs-2019"

Aşağıdaki örnek, 09260 mpc'si olan ve varsayılan yükleme konumunu varsayan Visual Studio 2019 Enterprise lisansı için `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`bir komut satırı gösterir:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 09260
```

::: moniker-end

::: moniker range="vs-2017"

 Aşağıdaki tablo, Visual Studio'nun her sürümü için MPC kodlarını listeler:

| Görsel Stüdyo Sürümü                | Mpc   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Uzmanı 2017 | 08866 |

::: moniker-end

::: moniker range="vs-2019"

| Görsel Stüdyo Sürümü                | Mpc   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2019        | 09260 |
| Visual Studio Professional 2019      | 09262 |

::: moniker-end

Ürün `StorePID.exe` anahtarı başarıyla uygulanırsa, `%ERRORLEVEL%` 0'ın bir kısmını döndürür. Hatalarla karşılaşırsa, hata durumuna bağlı olarak aşağıdaki kodlardan birini döndürür:

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
> Visual Studio'nun sanal bir örneğini çalıştırdığınızda, yerel AppData klasörünü ve kayıt defterini de sanallaştırdığınızdan emin olun. Sanal örnekleri gidermek için `C:\Program Files (x86)\Microsoft Visual Studio\<version>\Common7\IDE\DDConfigCA.exe`çalıştırın.  

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio yükleme](../install/install-visual-studio.md)
* [Visual Studio'nun çevrimdışı yüklemesini oluşturma](../install/create-an-offline-installation-of-visual-studio.md)
