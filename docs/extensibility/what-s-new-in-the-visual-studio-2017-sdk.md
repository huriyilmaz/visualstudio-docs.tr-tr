---
title: "&apos;Visual Studio 2017 SDK 'daki yenilikler | Microsoft Docs"
description: Visual Studio SDK, güncelleştirilmiş VSıX sürüm 3 biçimi de dahil olmak üzere Visual Studio 2017 için yeni ve güncelleştirilmiş özelliklere sahiptir.
ms.custom: SEO-VS-2020
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9ab9183eacfc82aa70c22dec551883561b021b58
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931256"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Visual Studio 2017 SDK 'sında ne&#39;yenidir

Visual Studio SDK, Visual Studio 2017 için aşağıdaki yeni ve güncelleştirilmiş özelliklere sahiptir.

## <a name="vsix-v3-format"></a>VSıX v3 biçimi

Visual Studio 2017 ' nin yeni hafif yüklemesini desteklemek için VSıX uzantısı bildirim biçimi sürüm 3 ' e (VSıX v3) güncelleştirilmiştir.

Yeni biçim şunları destekler:

* Algılanan önkoşulları açıkça bildirerek Valtıyükleyicisi tarafından yüklenir.
* Uzantı yüklemesinde Ngen derlemeleri.
* Varlıkları her zamanki uzantı kökünün dışında yükleme.

Bu değişiklikler hakkında bilgi edinmek için aşağıdaki konulara bakın:

* [Visual Studio 2017 için genişletilebilirlik değişiklikleri](breaking-changes-2017.md)
* [VSIX v3’te Ngen desteği](ngen-support.md)
* [Uzantılar klasörünün dışına yükleme](set-install-root.md)
* [Visual Studio 2017 genişletilebilirliği hakkında sık sorulan sorular](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Genişletilebilirlik projesini Visual Studio 2017 'ye geçirme

Genişletilebilirlik projelerinizi ve VSıX bildirimlerinizi Visual Studio 2017 ' e nasıl güncelleştireceğinizi öğrenmek için bkz. [nasıl yapılır: genişletilebilirlik projelerini Visual studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)' e geçirme.

## <a name="custom-project-and-item-templates"></a>Özel proje ve öğe şablonları

Visual Studio 2017 ' den başlayarak özel proje ve öğe şablonlarının taranması artık gerçekleştirilmeyecek. Bunun yerine, uzantı Bu şablonların yüklemesinin konumunu tanımlayan şablon bildirim dosyaları sağlamalıdır. VSıX uzantılarınızı güncelleştirmek için Visual Studio 2017 ' i kullanabilirsiniz. Uzantınızı bir MSI kullanarak dağıtırsanız, şablon bildirim dosyalarını el ile oluşturmanız gerekir. Daha fazla bilgi için bkz. [Visual Studio 2017 için özel proje ve öğe şablonlarını yükseltme](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Şablon bildirim şeması, [Visual Studio şablon bildirimi şema başvurusunda](../extensibility/visual-studio-template-manifest-schema-reference.md)belgelenmiştir.

## <a name="updated-extension-performance-guidelines"></a>Güncelleştirilmiş uzantı performans yönergeleri

Visual Studio başlatma ve çözüm yükleme saatlerinde uzantı etkisini algılamayı ve çözümlemeyi göstermek için [VSPackages](managing-vspackages.md) ' ın altındaki [uzantı performansını tanılama](how-to-diagnose-extension-performance.md) makalesini okuyun.
