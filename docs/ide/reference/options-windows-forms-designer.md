---
title: seçenekler, Windows Form Tasarımcısı, genel
description: kılavuzlar ve Visual Studio Windows Form Tasarımcısı diğer özelliklerine yönelik tercihleri ayarlamak için genel sayfasını kullanmayı öğrenin.
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
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: e263976523b85d5705bd9bbe324fa7e58c406c74381ead10c395ca935b9f7e9b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121447408"
---
# <a name="options-dialog-box-windows-forms-designer"></a>seçenekler iletişim kutusu: Windows Form Tasarımcısı

Windows Form Tasarımcısı seçenekleri sayfası, kılavuz ve Visual Studio Windows Form Tasarımcısı diğer özelliklerine yönelik tercihleri ayarlamanıza olanak sağlar. **Araçlar** menüsünden **Seçenekler** iletişim kutusunu açın.

## <a name="code-generation-settings"></a>kod oluşturma Ayarlar

**İyileştirilmiş kod oluşturma**\
İyileştirilmiş kod oluşturmayı sunar. Bazı denetimler bu modla uyumlu olmayabilir. bu değişikliğin etkili olabilmesi için Visual Studio kapatılıp yeniden açılması gerekir.

## <a name="high-dpi-support"></a>Yüksek DPı desteği

**DPı ölçeklendirme bildirimleri**\
Windows Form tasarımcısında, %100 ölçeklendirmeyle Visual Studio yeniden başlatabileceği bir ileti gösterin. Daha fazla bilgi için bkz. [VISUAL STUDIO DPI tanımayı devre dışı bırakma](/dotnet/framework/winforms/disable-dpi-awareness-visual-studio).

## <a name="layout-settings"></a>düzen Ayarlar

**Varsayılan Kılavuz hücre boyutu**\
Tasarımcıda yatay ve dikey kılavuz çizgileri arasındaki boşluğu piksel cinsinden ayarlar. Varsayılan boyut 8, 8 ' dir. En büyük boyut 200, 200 ' dir.

**Düzen modu**\
Düzen için kullanılacak hizalama sistemini belirtir. SnapToGrid veya snaplines seçeneklerinden birini belirleyebilirsiniz.

**Kılavuzu göster**\
Tasarımcıların boyutlandırma kılavuzunu görüntüleyip görüntülememediğini belirtir. Varsayılan olarak, kılavuz açık olur.

**Kılavuza yasla**\
Tasarımcıların nesneleri ve denetimleri kılavuza yapışıp uydurmayacağını belirler. Diğer bir deyişle, tasarımcıda öğelerin yeniden boyutlandırılması ve taşınması, bu özellik açık olduğunda GridSize artıcıyla sınırlıdır. SnapToGrid 'in açık olması, Kullanıcı arabiriminin çeşitli yönlerini kesin bir şekilde yerleştirmeyi kolaylaştırır, ancak bir denetimin yerleştirebileceği özgürlüğü kısıtlar. Varsayılan olarak, SnapToGrid açıktır.

## <a name="object-bound-smart-tag-settings"></a>nesne ile bağlantılı akıllı etiket Ayarlar

**Akıllı etiketleri otomatik olarak aç**\
Denetimlerin ve bileşenlerin Akıllı Etiketler görüntüleyip görüntülemediğini belirler. Tüm denetimler ve bileşenler akıllı etiketleri desteklemez.

## <a name="refactoring"></a>Yeniden Düzenle

**Yeniden adlandırma sırasında yeniden düzenlemeyi etkinleştir**\
Olarak ayarlandığında `true` , Özellikler penceresi veya belge anahattı penceresinden bir bileşeni yeniden adlandırdığınızda yeniden adlandırma yeniden düzenleme işlemi gerçekleştirilir.

## <a name="toolbox"></a>Araç Kutusu

**Araç kutusunu otomatik olarak doldur**\
Araç kutusu penceresinin, proje tarafından oluşturulan bileşenler ve denetimlerle otomatik olarak doldurulup doldurulmayacağını belirler.
