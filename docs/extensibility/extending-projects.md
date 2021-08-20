---
title: Projeleri Genişletme | Microsoft Docs
description: Visual Studio SDK'sı ile kendi özel proje türlerinizi oluşturma ve farklı türlerde Visual Studio öğrenin.
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
ms.openlocfilehash: 429c408fb54d77e9eb8705302f24880e27e84080
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122159366"
---
# <a name="extend-projects"></a>Projeleri genişletme
Projeler ve çözümler, kod ve Visual Studio derleme ve dağıtım birimlerinde düzenlemenin yollarıdır. Projeler (Visual Studio SDK) içinde [projeler hakkında daha fazla bilgi bulabilirsiniz.](../extensibility/extending-projects.md)

 Visual Studio SDK'sı ve Projeler için Yönetilen Paket Çerçevesi ile kendi proje türlerinizi oluşturabilirsiniz. Bunu Projeler için [Yönetilen Paket Çerçevesi'nde indirebilirsiniz.](https://github.com/tunnelvisionlabs/MPFProj10) Özel projelerin nasıl uygulandığını anlamak için [bkz. Yeni proje oluşturma:](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) Başlık altında, bölüm 1 ve [Yeni proje oluşturma: Başlık altında, ikinci bölüm.](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Bu bölümdeki konu başlıkları, özel projelerin nasıl oluşturularak farklı türlerde bir çözüm Visual Studio anlattır.

## <a name="in-this-section"></a>Bu bölümde
- [Temel proje sistemi oluşturma, bölüm 1](../extensibility/creating-a-basic-project-system-part-1.md) Özel bir proje sisteminin nasıl oluşturularak ilgili açıklamayı açıklar.

- [Temel proje sistemi oluşturma, bölüm 2](../extensibility/creating-a-basic-project-system-part-2.md) Özel bir proje sisteminin nasıl oluşturularak ilgili açıklamayı açıklar.

- [Proje dosyalarına veri kaydetme](../extensibility/saving-data-in-project-files.md) Projeye eklemeyi açıklar (<em>.</em> proj*) dosyaları.

- [Çalışma zamanında projenin alt türlerini doğrulama](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) Bir projenin çalışma zamanında alt türün nasıl doğrulanacaklarını açıklar.

- [Özellik sayfaları ekleme ve kaldırma](../extensibility/adding-and-removing-property-pages.md) Özel projeniz için özellik sayfalarını özelleştirmeyi açıklar.

- [Proje öğesine öznitelik ekleme](../extensibility/adding-an-attribute-to-a-project-item.md) Özel bir proje öğesine öznitelik eklemeyi açıklar.

- [Proje öğesinin özelliğini kalıcı olarak kalıcı olarak](../extensibility/persisting-the-property-of-a-project-item.md) Özel bir proje öğesinin özelliklerini kalıcı olarak nasıl kalıcı olarak bulundurabilirsiniz?

- [Evrensel Windows yönetme](../extensibility/managing-universal-windows-projects.md) Evrensel projeleri yönetmeyi açıklar.
