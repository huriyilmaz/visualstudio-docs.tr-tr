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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bf14fc4fec2d10f4bf7f9b8b26814680a9f42ba
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666387"
---
# <a name="options-dialog-box-visual-studio"></a>Seçenekler iletişim kutusu (Visual Studio)

**Seçenekler** iletişim kutusu, tümleşik geliştirme ORTAMıNı (IDE) gereksinimlerinize göre yapılandırmanızı sağlar. Örneğin, projeleriniz için varsayılan bir kaydetme konumu oluşturabilir, Windows 'un varsayılan görünümünü ve davranışını değiştirebilir ve yaygın olarak kullanılan komutlar için kısayollar oluşturabilirsiniz. Geliştirme diliniz ve platforma özgü seçenekler de vardır. **Seçeneklere** **Araçlar** menüsünden erişebilirsiniz.

## <a name="layout-of-the-options-dialog-box"></a>Seçenekler iletişim kutusunun düzeni

**Seçenekler** iletişim kutusu iki parçaya ayrılmıştır: sol taraftaki bir gezinti bölmesi ve sağ taraftaki bir görüntüleme alanı. Gezinti bölmesindeki ağaç denetimi, ortam, metin düzenleyici, projeler ve çözümler gibi klasör düğümlerini ve kaynak denetimini içerir. İçerdiği seçeneklerin sayfalarını listelemek için herhangi bir klasör düğümünü genişletin. Belirli bir sayfa için düğümü seçtiğinizde, seçenekleri görüntüleme alanında görüntülenir.

Özellik belleğe yüklenene kadar bir IDE özelliğinin seçenekleri gezinti bölmesinde görünmez. Bu nedenle, son ' u sonlandırmış olduğunuz sırada görüntülenen yeni bir oturuma başladığınızda aynı seçenekler görüntülenmeyebilir. Bir proje oluşturduğunuzda veya belirli bir uygulamayı kullanan bir komutu çalıştırdığınızda, ilgili seçeneklerin düğümleri Seçenekler iletişim kutusuna eklenir. Bu eklenen seçenekler, IDE özelliği bellekte kaldığı sürece kullanılabilir olmaya devam edecektir.

> [!NOTE]
> Bazı ayar koleksiyonları kapsam, Seçenekler iletişim kutusunun Gezinti bölmesinde görünen sayfa sayısını toplar. **Tüm ayarları göster**' i seçerek tüm olası sayfaları görüntülemeyi seçebilirsiniz.

## <a name="how-options-are-applied"></a>Seçenekler nasıl uygulanır

**Seçenekler** iletişim kutusunda Tamam ' a tıklamak tüm sayfalardaki tüm ayarları kaydeder. Herhangi bir sayfada Iptal ' i tıklamak diğer **Seçenekler** sayfalarında yapılan tüm değişiklik isteklerini iptal eder. Seçenek ayarları, [yazı tipleri ve renkler, ortam, Seçenekler Iletişim kutusu](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md)üzerinde yapılan değişiklikler gibi bazı değişiklikler yalnızca Visual Studio 'yu kapatıp yeniden açtıktan sonra devreye girer.

### <a name="show-all-settings"></a>Tüm ayarları göster

**Tüm ayarları göster** ' i seçmek veya seçimini kaldırmak, henüz **Tamam**' a tıklamasa bile, **Seçenekler** iletişim kutusunda yaptığınız tüm değişiklikleri uygular.

## <a name="see-also"></a>Ayrıca bkz.

- [Düzenleyiciyi Özelleştirme](../how-to-change-text-case-in-the-editor.md)