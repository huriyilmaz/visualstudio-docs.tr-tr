---
title: Seçenekler Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages
helpviewer_keywords:
- Tools Options settings
- Options dialog box
- Options dialog box, development environment
- tools [Visual Studio], customizing
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ed637943d7a849357338593ffc684e4f45c09a30
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662441"
---
# <a name="options-dialog-box-visual-studio"></a>Seçenekler İletişim Kutusu (Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Seçenekler** iletişim kutusu, tümleşik geliştirme ORTAMıNı (IDE) gereksinimlerinize göre yapılandırmanızı sağlar. Örneğin, projeleriniz için varsayılan bir kaydetme konumu oluşturabilir, Windows 'un varsayılan görünümünü ve davranışını değiştirebilir ve yaygın olarak kullanılan komutlar için kısayollar oluşturabilirsiniz. Geliştirme diliniz ve platforma özgü seçenekler de vardır. **Seçeneklere** **Araçlar** menüsünden erişebilirsiniz.

> [!NOTE]
> İletişim kutularında kullanılabilen seçenekler ve gördüğünüz menü komutlarının adları ve konumları, etkin ayarlarınıza veya sürümüne bağlı olarak yardım altında açıklananlar arasından farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="layout-of-the-options-dialog-box"></a>Seçenekler iletişim kutusunun düzeni
 **Seçenekler** iletişim kutusu iki parçaya ayrılmıştır: sol taraftaki bir gezinti bölmesi ve sağ taraftaki bir görüntüleme alanı. Gezinti bölmesindeki ağaç denetimi, ortam, metin düzenleyici, projeler ve çözümler gibi klasör düğümlerini ve kaynak denetimini içerir. İçerdiği seçeneklerin sayfalarını listelemek için herhangi bir klasör düğümünü genişletin. Belirli bir sayfa için düğümü seçtiğinizde, seçenekleri görüntüleme alanında görüntülenir.

 Özellik belleğe yüklenene kadar bir IDE özelliğinin seçenekleri gezinti bölmesinde görünmez. Bu nedenle, son ' u sonlandırmış olduğunuz sırada görüntülenen yeni bir oturuma başladığınızda aynı seçenekler görüntülenmeyebilir. Bir proje oluşturduğunuzda veya belirli bir uygulamayı kullanan bir komutu çalıştırdığınızda, ilgili seçeneklerin düğümleri Seçenekler iletişim kutusuna eklenir. Bu eklenen seçenekler, IDE özelliği bellekte kaldığı sürece kullanılabilir olmaya devam edecektir.

> [!NOTE]
> Bazı ayar koleksiyonları kapsam, Seçenekler iletişim kutusunun Gezinti bölmesinde görünen sayfa sayısını toplar. **Tüm ayarları göster**' i seçerek tüm olası sayfaları görüntülemeyi seçebilirsiniz.

## <a name="how-options-are-applied"></a>Seçenekler nasıl uygulanır
 **Seçenekler** iletişim kutusunda Tamam ' a tıklamak tüm sayfalardaki tüm ayarları kaydeder. Herhangi bir sayfada Iptal ' i tıklamak diğer **Seçenekler** sayfalarında yapılan tüm değişiklik isteklerini iptal eder. Seçenek ayarları, [yazı tipleri ve renkler, ortam, Seçenekler Iletişim kutusu](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md)üzerinde yapılan değişiklikler gibi bazı değişiklikler yalnızca Visual Studio 'yu kapatıp yeniden açtıktan sonra devreye girer.

### <a name="show-all-settings"></a>Tüm ayarları göster
 **Tüm ayarları göster** ' i seçmek veya seçimini kaldırmak, henüz **Tamam**' a tıklamasa bile, **Seçenekler** iletişim kutusunda yaptığınız tüm değişiklikleri uygular.

## <a name="see-also"></a>Ayrıca Bkz.
 [Düzenleyiciyi Özelleştirme](../../ide/customizing-the-editor.md)
