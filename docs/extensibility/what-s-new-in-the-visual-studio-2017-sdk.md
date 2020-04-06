---
title: Visual Studio 2017 SDK'da Neler&#39;| Microsoft Dokümanlar
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88330aa68f2a3752431fd2fbe6c5c1c649acbb8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697205"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Visual Studio 2017 SDK'da Neler&#39;Yeni

Visual Studio SDK, Visual Studio 2017 için aşağıdaki yeni ve güncel özelliklere sahiptir.

## <a name="vsix-v3-format"></a>VSIX v3 formatı

Visual Studio 2017'nin yeni hafif yüklemesini desteklemek için VSIX uzantı lı manifesto biçimi sürüm 3 'e (VSIX v3) güncelleştirildi.

Yeni biçim için destek vardır:

* VSIXInstaller tarafından tespit edilecek ve yüklenecek ön koşulları açıkça beyan etmek.
* Uzatma yüklemesi üzerinde Ngen derlemeleri.
* Varlıkları normal uzantı kökü dışında yükleme.

Bu değişiklikler hakkında bilgi edinmek için aşağıdaki konulara bakın:

* [Visual Studio 2017 için genişletilebilirlik değişiklikleri](breaking-changes-2017.md)
* [VSIX v3’te Ngen desteği](ngen-support.md)
* [Uzantılar klasörünün dışına yükleme](set-install-root.md)
* [Visual Studio 2017 genişletilebilirliği için sık sorulan sorular](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Genişletilebilirlik projesini Visual Studio 2017'ye geçirin

Genişletilebilirlik projelerinizi ve VSIX bildirimlerini Visual Studio 2017'ye nasıl güncelleştireceğimizi öğrenmek için [bkz.](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)

## <a name="custom-project-and-item-templates"></a>Özel proje ve madde şablonları

Visual Studio 2017'den itibaren özel proje ve öğe şablonları için tarama artık gerçekleştirilmeyecek. Bunun yerine, uzantı, bu şablonların yükleme konumunu açıklayan şablon bildirimi dosyaları sağlaması gerekir. VSIX uzantılarınızı güncellemek için Visual Studio 2017'yi kullanabilirsiniz. Uzantınızı bir MSI kullanarak dağıtırsanız, şablon bildirimi dosyalarını elle oluşturmanız gerekir. Daha fazla bilgi için [Visual Studio 2017 için Özel Proje yi Ve Öğe Şablonlarını Yükselt'e](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)bakın. Şablon bildirimi şeması Visual Studio [şablon ula'da belgelenmiştir.](../extensibility/visual-studio-template-manifest-schema-reference.md)

## <a name="updated-extension-performance-guidelines"></a>Güncelleştirilmiş uzantı performansı yönergeleri

Yeni bir [Nasıl Yapılır:](how-to-diagnose-extension-performance.md) Visual Studio başlatma ve çözüm yükleme süreleri üzerindeki uzantı etkisini nasıl algılayıp analiz edeceğimi göstermek için [VSPackages'i Yönet](managing-vspackages.md) altında uzantı performans makalesini tanılayın.
