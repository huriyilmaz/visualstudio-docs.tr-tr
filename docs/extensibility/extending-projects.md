---
title: Projeleri genişletme | Microsoft Docs
description: Visual Studio SDK 'da kendi özel proje türlerinizi oluşturmayı ve farklı türlerde Visual Studio çözümlerin nasıl yönetileceğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a6d7d93f4cd805db5bd161517c0af9a862457edb47aff912e6eab0afa7de0dbf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448357"
---
# <a name="extend-projects"></a>Projeleri genişletme
projeler ve çözümler, kod ve kaynak dosyalarını derleme ve dağıtım birimlerine göre düzenler Visual Studio yollar. projeler [(Visual Studio SDK)](../extensibility/extending-projects.md)hakkında daha fazla bilgi edinebilirsiniz.

 [projeler için yönetilen paket çerçevesinde](https://github.com/tunnelvisionlabs/MPFProj10)indirebileceğiniz Visual Studio SDK ve projeler için yönetilen paket çerçevesi ile kendi proje türlerinizi oluşturabilirsiniz. Özel projelerin nasıl uygulandığını anlamak için, bkz. [Yeni proje oluşturma: devlet, bölüm bir](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) ve [Yeni proje oluşturma altında: birinci, ikinci bölüm](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 bu bölümdeki konularda özel projeler oluşturma ve farklı Visual Studio çözüm türlerinin nasıl yönetileceği açıklanır.

## <a name="in-this-section"></a>Bu bölümde
- [Temel proje sistemi oluşturma, Bölüm 1](../extensibility/creating-a-basic-project-system-part-1.md) Özel bir proje sisteminin nasıl oluşturulacağını açıklar.

- [Temel proje sistemi oluşturma, Bölüm 2](../extensibility/creating-a-basic-project-system-part-2.md) Özel bir proje sisteminin nasıl oluşturulacağını açıklar.

- [Verileri proje dosyalarına kaydet](../extensibility/saving-data-in-project-files.md) Projenin nasıl ekleneceğini açıklar (<em>.</em> PROJ *) dosyaları.

- [Çalışma zamanında bir projenin alt türlerini doğrulama](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) Çalışma zamanında bir projenin alt türünün nasıl doğrulandığını açıklar.

- [Özellik sayfaları ekleme ve kaldırma](../extensibility/adding-and-removing-property-pages.md) Özel projeniz için özellik sayfalarının nasıl özelleştirileceğini açıklar.

- [Proje öğesine öznitelik ekleme](../extensibility/adding-an-attribute-to-a-project-item.md) Özel proje öğesine bir özniteliğin nasıl ekleneceğini açıklar.

- [Proje öğesinin özelliğini kalıcı hale](../extensibility/persisting-the-property-of-a-project-item.md) getirme Özel bir proje öğesinin özelliklerinin nasıl kalıcı yapılacağını açıklar.

- [evrensel Windows projelerini yönetme](../extensibility/managing-universal-windows-projects.md) Evrensel projelerin nasıl yönetileceğini açıklar.
