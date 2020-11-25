---
title: Seçenekler, Windows Form Tasarımcısı, genel
description: Visual Studio 'daki Windows Form Tasarımcısı ızgaraların ve diğer özelliklerinin tercihlerini ayarlamak için genel sayfasını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.General
helpviewer_keywords:
- Windows Forms Designer options
- Options dialog box, Windows Forms Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: d7172ca12344ab046c9bf65e7df280a9fa6dd0aa
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040088"
---
# <a name="options-dialog-box-windows-forms-designer"></a>Seçenekler iletişim kutusu: Windows Form Tasarımcısı

Windows Form Tasarımcısı seçenekleri sayfası, Visual Studio 'daki Windows Form Tasarımcısı kılavuzlar ve diğer özellikler için tercihleri ayarlamanıza olanak sağlar. **Araçlar** menüsünden **Seçenekler** iletişim kutusunu açın.

## <a name="code-generation-settings"></a>Kod oluşturma ayarları

**İyileştirilmiş kod oluşturma**\
İyileştirilmiş kod oluşturmayı sunar. Bazı denetimler bu modla uyumlu olmayabilir. Bu değişikliğin etkili olması için Visual Studio 'Nun kapatılıp yeniden açılması gerekir.

## <a name="high-dpi-support"></a>Yüksek DPı desteği

**DPı ölçeklendirme bildirimleri**\
Windows form tasarımcısında, Visual Studio 'Yu %100 ölçeklendirmeyle yeniden başlatabileceği bir ileti gösterin. Daha fazla bilgi için bkz. [Visual Studio 'DA DPI tanımayı devre dışı bırakma](/dotnet/framework/winforms/disable-dpi-awareness-visual-studio).

## <a name="layout-settings"></a>Düzen ayarları

**Varsayılan Kılavuz hücre boyutu**\
Tasarımcıda yatay ve dikey kılavuz çizgileri arasındaki boşluğu piksel cinsinden ayarlar. Varsayılan boyut 8, 8 ' dir. En büyük boyut 200, 200 ' dir.

**Düzen modu**\
Düzen için kullanılacak hizalama sistemini belirtir. SnapToGrid veya snaplines seçeneklerinden birini belirleyebilirsiniz.

**Kılavuzu göster**\
Tasarımcıların boyutlandırma kılavuzunu görüntüleyip görüntülememediğini belirtir. Varsayılan olarak, kılavuz açık olur.

**Kılavuza yasla**\
Tasarımcıların nesneleri ve denetimleri kılavuza yapışıp uydurmayacağını belirler. Diğer bir deyişle, tasarımcıda öğelerin yeniden boyutlandırılması ve taşınması, bu özellik açık olduğunda GridSize artıcıyla sınırlıdır. SnapToGrid 'in açık olması, Kullanıcı arabiriminin çeşitli yönlerini kesin bir şekilde yerleştirmeyi kolaylaştırır, ancak bir denetimin yerleştirebileceği özgürlüğü kısıtlar. Varsayılan olarak, SnapToGrid açıktır.

## <a name="object-bound-smart-tag-settings"></a>Nesne ile bağlantılı akıllı etiket ayarları

**Akıllı etiketleri otomatik olarak aç**\
Denetimlerin ve bileşenlerin Akıllı Etiketler görüntüleyip görüntülemediğini belirler. Tüm denetimler ve bileşenler akıllı etiketleri desteklemez.

## <a name="refactoring"></a>Yeniden Düzenle

**Yeniden adlandırma sırasında yeniden düzenlemeyi etkinleştir**\
Olarak ayarlandığında `true` , Özellikler penceresi veya belge anahattı penceresinden bir bileşeni yeniden adlandırdığınızda yeniden adlandırma yeniden düzenleme işlemi gerçekleştirilir.

## <a name="toolbox"></a>Araç Kutusu

**Araç kutusunu otomatik olarak doldur**\
Araç kutusu penceresinin, proje tarafından oluşturulan bileşenler ve denetimlerle otomatik olarak doldurulup doldurulmayacağını belirler.
