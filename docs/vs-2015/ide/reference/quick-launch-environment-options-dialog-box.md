---
title: Hızlı başlatma, ortam, Seçenekler Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.QuickLaunch
- vs.quicklaunch
helpviewer_keywords:
- searching IDE
- IDE, searching
ms.assetid: 4200f297-d065-4723-9a30-d91ff2e26c9d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: abd8f8e9ee35c234a79af74199b11d5491e6fbee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851628"
---
# <a name="quick-launch-environment-options-dialog-box"></a>Hızlı Başlatma, Ortam, Seçenekler İletişim Kutusu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Seçenekler, şablonlar, menüler gibi IDE varlıkları için eylemleri hızlıca aramak ve yürütmek üzere **Hızlı Başlat** ' ı kullanabilirsiniz. Kodu ve sembolleri aramak için **Hızlı başlatma** kullanamazsınız. **Hızlı Başlat** arama kutusu, menü çubuğunun sağ üst köşesinde bulunur ve CTRL + Q tuşları seçilerek erişilebilir. Arama dizenizi kutuya girmeniz yeterlidir. @ İçeren dizeleri aramak için ' @ @ ' kullanın.

 **Hızlı başlatma** , Visual Studio 'yu yüklediğinizde varsayılan olarak etkindir. Menü çubuğunda **Araçlar**, **Seçenekler**' i seçerek **hızlı başlatmayı** gösterebilir veya gizleyebilirsiniz. **Ortamlar** düğümünü genişletin ve **Hızlı Başlat**' ı seçin. **Hızlı başlatmayı etkinleştir** onay kutusunu seçin veya temizleyin. Ayrıca, bu sayfada arama kategorilerini etkinleştirebilir veya devre dışı bırakabilirsiniz.

## <a name="category-list"></a>Kategori listesi
 Hızlı başlatma arama sonuçları dört kategoride görünür: **en son kullanılanlar**, **menüler**, **Seçenekler**ve **Açık belgeler**, kategori içindeki öğe sayısı ile birlikte. Arama sonuçları arasında kategoriye göre gezinmek için, sonraki kategorinin tüm sonuçlarını göstermek için CTRL + Q tuşlarını seçin. Son kategori görüntülendikten sonra CTRL + Q, her kategoriden birkaç sonuç gösterir. Kategoriler arasında ters sırada gezinmek için CTRL + SHIFT + Q kullanabilirsiniz. Bir kategori altındaki tüm arama sonuçlarını görüntülemek için kategori adını seçin.

 Aramanızı belirli kategorilere sınırlamak için aşağıdaki kısayolları kullanabilirsiniz.

|Kategori|Kısayol|Kısayol açıklaması|
|--------------|--------------|--------------------------|
|En son kullanılan|@mru<br /><br /> Örneğin, `@mru font`|**En son kullandığınız**öğelerin en fazla beş sayısını görüntüler.|
|Menüler|@menu<br /><br /> Örneğin, `@menu font`|Aramayı menü öğeleriyle sınırlandırır.|
|Seçenekler|@opt<br /><br /> Örneğin, `@opt font`|**Seçenekler** iletişim kutusundaki arama ayarlarını sınırlandırır.|
|Belgeler|@doc<br /><br /> Örneğin, `@doc font`|Arama kriterlerine yönelik açık belgelerin dosya adlarıyla ve yollarına yönelik aramayı kısıtlar, ancak dosyaların içinde metinde arama yapmaz.|

> [!NOTE]
> **Seçenekler** Iletişim kutusundaki **genel**, **klavye** sayfasında kısayol tuşlarını değiştirebilirsiniz.

## <a name="show-previous-results"></a>Önceki sonuçları göster
 Varsayılan olarak, girdiğiniz arama terimi arama oturumları arasında kalıcı olmaz. Arama dizesi bir terim arıyorsanız, imleci **Hızlı başlatma** alanının dışına taşıyın ve ardından geri dönün. Arama sonuçlarını sürdürmek için **Seçenekler** iletişim kutusuna gidin, **Hızlı Başlat**' ı seçin ve ardından **Hızlı başlatma etkinleştirildiğinde önceki aramadan arama sonuçlarını göster** ' i seçin. onay kutusunu işaretleyin. Bir sonraki sefer bir arama yaptığınızda hızlı başlatma alanını bırakın ve geri dönüp, hızlı başlatma en son kullanılan arama terimini korur ve ayrıca arama sonuçlarını gösterir.

 **Hızlı başlatma**kullanmaya yönelik en son ipuçları ve püf noktaları için bkz. [Visual Studio blogu](https://blogs.msdn.com/b/visualstudio/).

## <a name="see-also"></a>Ayrıca Bkz.
 [Genel kullanıcı arabirimi öğeleri (Visual Studio)](../../ide/reference/general-user-interface-elements-visual-studio.md) [ortam seçenekleri iletişim kutusu](../../ide/reference/environment-options-dialog-box.md)
