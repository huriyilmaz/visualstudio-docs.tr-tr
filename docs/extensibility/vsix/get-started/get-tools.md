---
title: Araçları elde edin
description: Uzantılar ve yükleme hakkında Visual Studio araçların listesi.
ms.date: 12/01/2021
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: pchapman
ms.prod: visual-studio-windows
ms.technology: vs-ide-sdk
ms.custom: cookbook
ms.openlocfilehash: 51a05667664de6bfc30d910974c70139709e96a3
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133516633"
---
# <a name="get-the-tools-needed-to-write-visual-studio-extensions"></a>Uzantı yazmak için gereken Visual Studio al

Uzantı yazmak için genişletilebilirlik iş yükünü yüklemeniz gerekir. Teknik olarak tek ihtiyacınız olan bu ama bu belge kümesi Genişletilebilirlik Temel Bilgileri adlı topluluk *odaklı uzantıyı kullanır.* Her bir Visual Studio sürümü kendi sürümüne sahip: [Genişletilebilirlik TemelLeri 2019](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.ExtensibilityEssentials2019) veya [Genişletilebilirlik TemelLeri 2022](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.ExtensibilityEssentials2022).

Aşağıdaki videoda ihtiyacınız olacak araçlar tanıt açıklamalır.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWPhtT]

## <a name="install-extensibility-workload"></a>Genişletilebilirlik iş yükünü yükleme

İlkeyi **açmak Visual Studio Yükleyicisi** Araçlar'ı **ve** ardından Araçları ve Özellikleri **Al... 'ı seçin.** Ardından uzantı geliştirme **Visual Studio yüklerini** yükleyin.

:::image type="content" source="../media/visual-studio-installer.png" alt-text="Genişletilebilirlik iş yükünü gösteren VS Yükleyicisi.":::

## <a name="install-extensibility-essentials"></a>Genişletilebilirlik TemelLerini Yükleme
Genişletilebilirlik **TemelLeri'yi yüklemek** için **Uzantılar'ı** seçin, Uzantıları **Yönet'i seçin** ve *genişletilebilirlik araması yapabilirsiniz.*

* 2019 Visual Studio Genişletilebilirlik TemelLeri [2019'a yükleyin.](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.ExtensibilityEssentials2019)
* 2022 Visual Studio için [Genişletilebilirlik TemelLeri 2022 yükleyin.](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.ExtensibilityEssentials2022)

:::image type="content" source="../media/install-extensibility-essentials.png" alt-text="Uzantı Yöneticisi iletişim kutusundan Genişletilebilirlik TemelLeri'ni yükleyin.":::

İşte bu kadar, artık ilk uzantınızı geliştirmeye [başlamaya hazır olursanız.](first-extension.md)
