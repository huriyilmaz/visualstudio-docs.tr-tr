---
title: Seçenekler iletişim kutusu
description: Seçenekler iletişim kutusu, düzeni ve Visual Studio'ların, projelerinize ve çözümlerinize hangi seçeneklerin uygulanacağı hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages
helpviewer_keywords:
- Tools Options settings
- Options dialog box
- Options dialog box, development environment
- tools [Visual Studio], customizing
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 65da75976642997f626de1aeeab52b4d88a948fa
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627212"
---
# <a name="options-dialog-box-visual-studio"></a>Seçenekler iletişim kutusu (Visual Studio)

Seçenekler **iletişim** kutusu, tümleşik geliştirme ortamını (IDE) ihtiyaçlarınıza göre yapılandırmanızı sağlar. Örneğin, projeleriniz için varsayılan bir kaydetme konumu oluşturabilir, pencerelerin varsayılan görünümünü ve davranışını değiştirebilir ve yaygın olarak kullanılan komutlar için kısayollar oluşturabilirsiniz. Geliştirme dilinize ve platforma özgü seçenekler de vardır. Seçenekler'e **Araçlar** **menüsünden erişebilirsiniz.**

## <a name="layout-of-the-options-dialog-box"></a>Seçenekler iletişim kutusunun düzeni

Seçenekler  iletişim kutusu iki bölüme ayrılır: sol tarafta bir gezinti bölmesi ve sağ tarafta bir görüntüleme alanı. Gezinti bölmesindeki ağaç denetimi Ortam, Metin Düzenleyici, Projeler ve Çözümler ve Kaynak Denetimi gibi klasör düğümlerini içerir. Içerdiği seçeneklerin sayfalarını listeleyecek herhangi bir klasör düğümünü genişletin. Belirli bir sayfanın düğümünü seçerek görüntüleme alanında seçenekleri görüntülenir.

IDE özelliğinin seçenekleri, özellik belleğe yüklenene kadar gezinti bölmesinde görünmez. Bu nedenle, en son sona ermiştiniz gibi görüntülenen yeni bir oturuma başlarken aynı seçenekler görüntülenmeyebilirsiniz. Bir proje oluşturma veya belirli bir uygulamayı kullanan bir komut çalıştırma, ilgili seçenekler için düğümler Seçenekler iletişim kutusuna eklenir. Bu eklenen seçenekler, IDE özelliği bellekte olduğu sürece kullanılabilir olmaya devam ediyor.

> [!NOTE]
> Bazı ayarlar koleksiyonları, Seçenekler iletişim kutusunun gezinti bölmesinde görünen sayfa sayısını kapsamına almaktadır.

## <a name="how-options-are-applied"></a>Seçeneklerin uygulanması

Seçenekler iletişim kutusunda **Tamam'a** tıklamak tüm sayfalara tüm ayarları kaydeder. Herhangi bir sayfada İptal'e tıklamak, diğer Seçenekler sayfalarında yapılanlar da dahil olmak üzere tüm değişiklik **isteklerini iptal** eder. Yazı Tipleri ve Renkler, Ortam, Seçenekler İletişim Kutusu gibi seçenek ayarlarında yapılan bazı [değişiklikler,](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md)yalnızca ilgili ayarları kapatıp yeniden açtıktan sonra Visual Studio.

## <a name="see-also"></a>Ayrıca bkz.

- [Düzenleyiciyi Özelleştirme](../how-to-change-text-case-in-the-editor.md)
- [Git ayarları ve tercihleri](../../version-control/git-settings.md)
