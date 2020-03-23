---
title: Seçenekler iletişim kutusu
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c864a10af9ad15d47e2342bb148af464b8f2a0d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591508"
---
# <a name="options-dialog-box-visual-studio"></a>Seçenekler iletişim kutusu (Visual Studio)

**Seçenekler** iletişim kutusu, tümleşik geliştirme ortamını (IDE) gereksinimlerinize göre yapılandırmanızı sağlar. Örneğin, projeleriniz için varsayılan bir kaydet konumu oluşturabilir, pencerelerin varsayılan görünümünü ve davranışını değiştirebilir ve sık kullanılan komutlar için kısayollar oluşturabilirsiniz. Geliştirme dilinize ve platformunuza özel seçenekler de vardır. **Araçlar** menüsünden **Seçenekler'e** erişebilirsiniz.

## <a name="layout-of-the-options-dialog-box"></a>Seçenekler iletişim kutusunun düzeni

**Seçenekler** iletişim kutusu iki bölüme ayrılmıştır: solda bir gezinti bölmesi ve sağda bir görüntü alanı. Gezinti bölmesindeki ağaç denetimi, Çevre, Metin Düzenleyicisi, Projeler ve Çözümler ve Kaynak Denetimi gibi klasör düğümlerini içerir. İçindebulunduğu seçeneklerin sayfalarını listelemek için herhangi bir klasör düğümünü genişletin. Belirli bir sayfanın düğümünü seçtiğinizde, seçenekleri görüntü alanında görünür.

Özellik belleğe yüklenene kadar bir IDE özelliği seçenekleri gezinti bölmesinde görünmez. Bu nedenle, en son sona ererken görüntülenen yeni bir oturuma başlarken aynı seçenekler görüntülenmeyebilir. Bir proje oluşturduğunuzda veya belirli bir uygulamayı kullanan bir komut çalıştırdığınızda, ilgili seçenekler için düğümler Seçenekler iletişim kutusuna eklenir. Bu eklenen seçenekler, IDE özelliği bellekte kaldığı sürece kullanılabilir durumda kalır.

> [!NOTE]
> Bazı ayarlar koleksiyonları, Seçenekler iletişim kutusunun gezinti bölmesinde görünen sayfa sayısını gösterir. **Tüm ayarları göster'i**seçerek tüm olası sayfaları görüntülemeyi seçebilirsiniz.

## <a name="how-options-are-applied"></a>Seçenekler nasıl uygulanır?

**Seçenekler** iletişim kutusunda Tamam'ı tıklattığınızda tüm sayfalardaki tüm ayarları kaydeder. Herhangi bir sayfada İptal'i tıklattığınızda, diğer **Seçenekler** sayfalarında yapılanlar da dahil olmak üzere tüm değişiklik istekleri iptal edilir. [Yazı Tipleri ve Renkler, Çevre, Seçenekler İletişim Kutusu'nda](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md)yapılanlar gibi seçenek ayarlarında yapılan bazı değişiklikler, visual studio'yu kapatıp yeniden açtıktan sonra etkili olur.

### <a name="show-all-settings"></a>Tüm ayarları göster

Seçişimdi veya seçimi yapmak Henüz **Tamam'ı**tıklatmamış olsanız **bile, Seçenekler** iletişim kutusunda yaptığınız tüm değişiklikleri **göster'** i seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Düzenleyiciyi Özelleştirme](../how-to-change-text-case-in-the-editor.md)
