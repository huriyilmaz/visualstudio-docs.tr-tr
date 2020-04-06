---
title: Proje Türlerinin Dağıtılması | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 835e85ade4d309d0b5692aa9b857476cd6b5927a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708782"
---
# <a name="deploy-project-types"></a>Proje türlerini dağıtma
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]yeni bir proje tipi toplayıcı *(ProjectAggregator2.dll)* ve yeniden dağıtım için bir Windows Yükleyici paketi *(ProjectAggregator2.msi)* yükler. Yönetilen kod proje türleri için yeni toplayıcı kullanmanız gerekir. ProjectAggregator2, yönetilen kod [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proje türlerinin doğru çalışmasını engelleyen proje toplayıcısındaki sınırlamalar etrafında çalışır. Aşağıdaki adımlar, yeni toplayıcıyı kullanmak için VSPackage'ınızı nasıl değiştireceğinizaçıklanmıştır.

1. NativeHiyerarşiWrapper projesini çözümünüzden kaldırın.

2. Herhangi bir NativeHiyerarşiWrapper ikililerini kurulumunuzdan kaldırın.

3. Kurulumunuza *ProjectAggregator2.msi* ekleyin.
