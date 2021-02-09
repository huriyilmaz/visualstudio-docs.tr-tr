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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e21c5b8a3570b4da0cb0286d3c0d6d7c84c2f704
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895849"
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
