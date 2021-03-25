---
title: Proje türlerini dağıtma | Microsoft Docs
description: Visual Studio SDK 'sında yeni bir proje türü toplayıcısı ve yeniden dağıtım için Windows Installer paketi kullanarak yönetilen kod proje türlerini dağıtmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 121dda58b8e01c5b0029d8b3c93ef66d2657446e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090999"
---
# <a name="deploy-project-types"></a>Proje türlerini dağıt
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Yeni bir proje türü toplayıcısı (*ProjectAggregator2.dll*) ve ayrıca yeniden dağıtım için bir Windows Installer paketi (*ProjectAggregator2.msi*) yüklenir. Yönetilen kod proje türleri için yeni toplayıcısı 'nı kullanmanız gerekir. ProjectAggregator2, proje toplayıcısı 'nda, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yönetilen kod proje türlerinin düzgün çalışmasını engelleyen sınırlamalar çerçevesinde çalışır. Aşağıdaki adımlarda, VSPackage 'ın yeni toplayıcısı 'nı kullanacak şekilde nasıl değiştirileceği açıklanır.

1. NativeHierarchyWrapper projesini çözümünüzden kaldırın.

2. Tüm NativeHierarchyWrapper ikililerini kurulumınızdan kaldırın.

3. *ProjectAggregator2.msi* , kuruluma ekleyin.
