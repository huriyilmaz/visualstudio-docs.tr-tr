---
title: Visual Studio 'nun diğer kısımlarını genişletme | Microsoft Docs
description: Visual Studio Kullanıcı arabiriminin genişletebileceğinizi parçalar hakkında bilgi edinin. Bir VSPackage oluşturabilir, etkinlik günlüğüne yazabilir ve araç kutusunu ve durum çubuğunu genişletebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces
ms.assetid: 27d2f1e1-2503-4aca-9cfc-707abd07ccf0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 193fb335ffd2d57eab1aebedc5ea0114738f72eb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075243"
---
# <a name="extend-other-parts-of-visual-studio"></a>Visual Studio 'nun diğer kısımlarını genişletme

Visual Studio Kullanıcı arabiriminin genişletebilmeniz için daha birçok bölümü vardır. Burada yalnızca birkaç tane gösterilmektedir.

## <a name="create-a-vspackage"></a>VSPackage oluşturma

Visual Studio genişletilebilirliğine yönelik temel yapı taşları VSPackages 'dir.  VSPackage ekleme hakkında bilgi edinin: [VSPackage ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-vspackage.md)

## <a name="extend-the-toolbox"></a>Araç kutusunu genişletme

Araç kutusuna yeni denetimler ve diğer öğeler eklemeyi ve araç kutusu işlevselliğinin nasıl kullanılacağını öğrenin:

- [WPF araç kutusu denetimi oluşturma](../extensibility/creating-a-wpf-toolbox-control.md)

- [Windows Forms araç kutusu denetimi oluşturma](../extensibility/creating-a-windows-forms-toolbox-control.md)

## <a name="extend-the-status-bar"></a>Durum çubuğunu genişletme

Durum çubuğunu ve ilerleme çubuğunu okumayı ve yazmayı, animasyonları ve diğer Kullanıcı arabirimini nasıl sağlayacağınızı öğrenin: [durum çubuğunu genişletme](../extensibility/extending-the-status-bar.md).

::: moniker range="vs-2017"

## <a name="create-custom-start-pages"></a>Özel başlangıç sayfaları oluşturma

Kendi başlangıç sayfanızı sıfırdan veya indirilebilir bir başlangıç sayfasından nasıl yapacağınızı öğrenin örnek: [özel başlangıç sayfası oluşturma](../extensibility/creating-a-custom-start-page.md).

::: moniker-end

## <a name="write-to-the-activity-log"></a>Etkinlik günlüğüne yaz

Etkinlik günlüğüne yazmayı öğrenin: [nasıl yapılır: etkinlik günlüğünü kullanma](../extensibility/how-to-use-the-activity-log.md).
