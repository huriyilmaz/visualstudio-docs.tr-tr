---
title: Projeleri genişletme | Microsoft Docs
description: Visual Studio SDK 'da kendi özel proje türlerinizi oluşturmayı ve farklı türlerde Visual Studio çözümlerini yönetmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 181acea9a5188ba28a4ef109b5bec0e7c040b5da
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994621"
---
# <a name="extend-projects"></a>Projeleri genişletme
Projeler ve çözümler, Visual Studio 'Nun kod ve kaynak dosyalarını derleme ve dağıtım birimlerine düzenleridir. Projelerde projeler hakkında daha fazla bilgi edinebilirsiniz [(Visual STUDIO SDK)](../extensibility/extending-projects.md).

 Visual Studio SDK ile kendi proje türlerinizi ve projeler için yönetilen [paket çatısı](https://github.com/tunnelvisionlabs/MPFProj10)' nı Indirebileceğiniz projeler Için yönetilen paket çerçevesi oluşturabilirsiniz. Özel projelerin nasıl uygulandığını anlamak için, bkz. [Yeni proje oluşturma: devlet, bölüm bir](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) ve [Yeni proje oluşturma altında: birinci, ikinci bölüm](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Bu bölümdeki konularda özel projeler oluşturma ve farklı türde Visual Studio çözümünün nasıl yönetileceği açıklanır.

## <a name="in-this-section"></a>Bu bölümde
- [Temel proje sistemi oluşturma, Bölüm 1](../extensibility/creating-a-basic-project-system-part-1.md) Özel bir proje sisteminin nasıl oluşturulacağını açıklar.

- [Temel proje sistemi oluşturma, Bölüm 2](../extensibility/creating-a-basic-project-system-part-2.md) Özel bir proje sisteminin nasıl oluşturulacağını açıklar.

- [Verileri proje dosyalarına kaydet](../extensibility/saving-data-in-project-files.md) Projenin nasıl ekleneceğini açıklar (<em>.</em> PROJ *) dosyaları.

- [Çalışma zamanında bir projenin alt türlerini doğrulama](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) Çalışma zamanında bir projenin alt türünün nasıl doğrulandığını açıklar.

- [Özellik sayfaları ekleme ve kaldırma](../extensibility/adding-and-removing-property-pages.md) Özel projeniz için özellik sayfalarının nasıl özelleştirileceğini açıklar.

- [Proje öğesine öznitelik ekleme](../extensibility/adding-an-attribute-to-a-project-item.md) Özel proje öğesine bir özniteliğin nasıl ekleneceğini açıklar.

- [Proje öğesinin özelliğini kalıcı hale](../extensibility/persisting-the-property-of-a-project-item.md) getirme Özel bir proje öğesinin özelliklerinin nasıl kalıcı yapılacağını açıklar.

- [Evrensel Windows projelerini yönetme](../extensibility/managing-universal-windows-projects.md) Evrensel projelerin nasıl yönetileceğini açıklar.
