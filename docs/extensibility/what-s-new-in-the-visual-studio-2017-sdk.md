---
title: "&apos;Visual Studio 2017 SDK'sı | Microsoft Docs"
description: Visual Studio SDK, güncelleştirilmiş VSIX sürüm 3 biçimi de dahil olmak üzere Visual Studio 2017 için yeni ve güncelleştirilmiş özelliklere sahiptir.
ms.custom: SEO-VS-2020
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 90b1bb8406524a9c3ea9a3fb5eb0058070915e7b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122056582"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Visual Studio 2017 SDK&#39;ki Yeni Uygulamalar

Visual Studio SDK, Visual Studio 2017 için aşağıdaki yeni ve güncelleştirilmiş özelliklere sahiptir.

## <a name="vsix-v3-format"></a>VSIX v3 biçimi

Visual Studio 2017'nin yeni hafif yüklemesini desteklemek için VSIX uzantısı bildirim biçimi sürüm 3'e (VSIX v3) güncelleştirilmiştir.

Yeni biçimin desteği vardır:

* VSIXInstaller tarafından algılanan ve yüklenmek için önkoşulları açıkça bildirerek.
* Uzantı yüklemesi üzerinde Ngen derlemeleri.
* Varlıkları normal uzantı kökü dışında yükleme.

Bu değişiklikler hakkında bilgi edinmek için aşağıdaki konulara bakın:

* [Visual Studio 2017 için genişletilebilirlik değişiklikleri](breaking-changes-2017.md)
* [VSIX v3’te Ngen desteği](ngen-support.md)
* [Uzantılar klasörünün dışına yükleme](set-install-root.md)
* [2017 genişletilebilirliği Visual Studio sık sorulan sorular](faq-2017.yml)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Genişletilebilirlik projesini Visual Studio 2017'ye geçirme

Genişletilebilirlik projelerinizi ve VSIX bildirimlerini Visual Studio 2017'ye güncelleştirme hakkında bilgi edinmek için bkz. Nasıl yapılır: Genişletilebilirlik projelerini [Visual Studio 2017'ye](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)geçirme.

## <a name="custom-project-and-item-templates"></a>Özel proje ve öğe şablonları

2017'Visual Studio başlayarak özel proje ve öğe şablonları için tarama artık gerçekleştirilmeyecek. Bunun yerine, uzantının bu şablonların yükleme konumunu açıklayan şablon bildirim dosyaları sağlaması gerekir. VSIX uzantılarınızı güncelleştirmek Visual Studio 2017'de kullanabilirsiniz. Uzantınızı bir MSI kullanarak dağıtırsanız şablon bildirim dosyalarını el ile oluşturabilirsiniz. Daha fazla bilgi için, [bkz. Upgrade custom project and item templates for Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Şablon bildirimi şeması, şablon bildirim [Visual Studio başvurusunda belgelenmiş.](../extensibility/visual-studio-template-manifest-schema-reference.md)

## <a name="updated-extension-performance-guidelines"></a>Uzantı performansı yönergeleri güncelleştirildi

Uzantının [başlangıç](how-to-diagnose-extension-performance.md) ve çözüm yükleme sürelerini algılama ve analiz etme hakkında bilgi için [VSPackage'ları](managing-vspackages.md) Yönetme altında yeni bir Nasıl Visual Studio tanılama makalesi vardır.
