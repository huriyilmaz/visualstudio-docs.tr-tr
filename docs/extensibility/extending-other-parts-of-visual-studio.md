---
title: Visual Studio 'nun diğer kısımlarını genişletme | Microsoft Docs
description: Visual Studio Kullanıcı arabiriminin genişletebileceğinizi parçalar hakkında bilgi edinin. Bir VSPackage oluşturabilir, etkinlik günlüğüne yazabilir ve araç kutusunu ve durum çubuğunu genişletebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces
ms.assetid: 27d2f1e1-2503-4aca-9cfc-707abd07ccf0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7cc9a471b141cfd3302814844d63a2ce8d5b74c6
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995843"
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
