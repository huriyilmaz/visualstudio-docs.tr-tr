---
title: Projelerin Genişletilmesi | Microsoft Dokümanlar
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
ms.openlocfilehash: 14108a304cc5f85c9a870bc66804df7daa98f3ca
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711746"
---
# <a name="extend-projects"></a>Projeleri genişletme
Projeler ve çözümler Visual Studio'nun kod ve kaynak dosyalarını derleme ve dağıtım birimleri olarak düzenleme yöntemleridir. [Projeler (Visual Studio SDK)](../extensibility/extending-projects.md)projeleri hakkında daha fazla bilgi bulabilirsiniz.

 Visual Studio SDK ve [Projeler](https://github.com/tunnelvisionlabs/MPFProj10)için Yönetilen Paket Çerçevesi ile kendi proje türlerinizi oluşturabilirsiniz. Özel projelerin nasıl uygulandığını anlamak için [bkz: Yeni proje oluşturma: Başlık altında, bölüm bir](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) ve [Yeni proje üretimi: Başlık altında, ikinci bölüm](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Bu bölümdeki konular, özel projelerin nasıl oluşturulup yönetilenleri ve farklı Görsel Stüdyo çözüm türlerinin nasıl yönetilenlerini açıklar.

## <a name="in-this-section"></a>Bu bölümde
- [Temel bir proje sistemi oluşturma, bölüm 1](../extensibility/creating-a-basic-project-system-part-1.md) Özel bir proje sisteminin nasıl oluşturuluruz açıklanır.

- [Temel bir proje sistemi oluşturma, bölüm 2](../extensibility/creating-a-basic-project-system-part-2.md) Özel bir proje sisteminin nasıl oluşturuluruz açıklanır.

- [Proje dosyalarına veri kaydetme](../extensibility/saving-data-in-project-files.md) Projeye nasıl ekleyeceğini açıklar (<em>.</em> proj*) dosyaları.

- [Projenin alt türlerini çalışma zamanında doğrulama](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) Bir projenin alt türünün çalışma zamanında nasıl doğrulanınan ını açıklar.

- [Özellik sayfaları ekleme ve kaldırma](../extensibility/adding-and-removing-property-pages.md) Özel projeniz için özellik sayfalarını nasıl özelleştiriştireceklerini açıklar.

- [Proje öğesine öznitelik ekleme](../extensibility/adding-an-attribute-to-a-project-item.md) Özel bir proje öğesine nasıl öznitelik ekleyeceğini açıklar.

- [Proje öğesinin özelliğini devam etti](../extensibility/persisting-the-property-of-a-project-item.md) Özel bir proje öğesinin özelliklerini nasıl devam ettireceklerini açıklar.

- [Evrensel Windows projelerini yönetme](../extensibility/managing-universal-windows-projects.md) Evrensel projelerin nasıl yönetilenini açıklar.
