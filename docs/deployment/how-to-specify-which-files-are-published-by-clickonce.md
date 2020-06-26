---
title: ClickOnce tarafından hangi dosyaların yayımlandığını belirleme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.File
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, file exclusion
- files, publishing via ClickOnce
ms.assetid: 579c134a-d50f-4e0c-8e05-2a4ff654896a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7ab6d724b40168f84227edb6ccfafc6245c30e0
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85381788"
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>Nasıl yapılır: ClickOnce tarafından hangi dosyaların yayımlandığını belirtme
Bir uygulamayı yayımlarken [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , projedeki tüm kod olmayan dosyalar uygulamayla birlikte dağıtılır. Bazı durumlarda, belirli dosyaları yayımlamanıza veya yayımlamanız gerekebilir ya da koşullara göre belirli dosyaları yüklemek isteyebilirsiniz. Visual Studio, dosyaları hariç tutma, dosyaları veri dosyaları veya önkoşulları olarak işaretleme ve koşullu yükleme için dosya grupları oluşturma olanakları sağlar.

 Uygulama dosyaları, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] **Proje Tasarımcısı**' nın **Yayımla** sayfasından erişilebilen **uygulama dosyaları** iletişim kutusunda yönetilir.

 Başlangıçta, **(gerekli)** adlı tek bir dosya grubu vardır. Ek dosya grupları oluşturabilir ve bunlara dosya atayabilirsiniz. Uygulamanın çalışması için gerekli olan dosyalar için **Indirme grubunu** değiştiremezsiniz. Örneğin, uygulamanın. exe dosyası veya veri dosyası olarak işaretlenmiş dosyalar **(gerekli)** grubuna ait olmalıdır.

 Bir dosyanın varsayılan yayımlama durumu değeri **(Auto)** ile etiketlenir. Örneğin, uygulamanın. exe ' nin, varsayılan olarak **Ekle (otomatik)** yayımlama durumu vardır.

 **Yapı eylemi** özelliği **içeriğe** ayarlanmış olan dosyalar, uygulama dosyaları olarak atanır ve varsayılan olarak dahil edilir. Bunlar dahil edilebilir, hariç tutulabilir veya veri dosyaları olarak işaretlenebilir. Özel durumlar aşağıdaki gibidir:

- SQL veritabanı (*. mdf* ve *. mdb*) dosyaları ve XML dosyaları gibi veri dosyaları varsayılan olarak veri dosyaları olarak işaretlenir.

- Başvuruya eklediğiniz derlemeler (*. dll* dosyaları) başvuruları aşağıdaki şekilde atanır: yereli **Kopyala** **yanlış**ise, uygulama yüklenmeden önce GAC 'de bulunması gereken önkoşul derlemesi (**Önkoşul (otomatik)**) olarak varsayılan olarak işaretlenir. Yereli **Kopyala** **true**ise, derleme varsayılan olarak bir uygulama derlemesi (**dahil et (otomatik)**) olarak işaretlenir ve yükleme sırasında uygulama klasörüne kopyalanır. Bir COM başvurusu, **uygulama dosyaları** iletişim kutusunda ( *. ocx* dosyası olarak) yalnızca **Isolated** özelliği **true**olarak ayarlandığında görüntülenir. Varsayılan olarak, dahil edilir.

### <a name="to-add-files-to-the-application-files-dialog-box"></a>Uygulama dosyaları iletişim kutusuna dosya eklemek için

1. **Çözüm Gezgini**bir veri dosyası seçin.

2. Özellikler penceresi, **Yapı eylemi** özelliğini **içerik** değeri olarak değiştirin.

### <a name="to-exclude-files-from-clickonce-publishing"></a>ClickOnce yayımcılarından dosyaları dışlamak için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Uygulama dosyaları iletişim kutusunu** açmak Için **uygulama dosyaları** düğmesine tıklayın.

4. **Uygulama dosyaları** iletişim kutusunda dışlamak istediğiniz dosyayı seçin.

5. **Yayımlama durumu** alanında, açılan listeden **hariç tut** ' u seçin.

### <a name="to-mark-files-as-data-files"></a>Dosyaları veri dosyası olarak işaretlemek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Uygulama dosyaları iletişim kutusunu** açmak Için **uygulama dosyaları** düğmesine tıklayın.

4. **Uygulama dosyaları** iletişim kutusunda, veri olarak işaretlemek istediğiniz dosyayı seçin.

5. **Yayımlama durumu** alanında, açılan listeden **veri dosyası** ' nı seçin.

### <a name="to-mark-files-as-prerequisites"></a>Dosyaları önkoşul olarak işaretlemek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Uygulama dosyaları iletişim kutusunu** açmak Için **uygulama dosyaları** düğmesine tıklayın.

4. **Uygulama dosyaları** iletişim kutusunda, önkoşul olarak işaretlemek istediğiniz uygulama derlemesini (*. dll* dosyası) seçin. Uygulamanızın, listede görünmesi için uygulama derlemesine bir başvuruya sahip olması gerektiğini unutmayın.

5. **Yayımlama durumu** alanında, açılan listeden **Önkoşul** ' i seçin.

### <a name="to-add-a-new-file-group"></a>Yeni bir dosya grubu eklemek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Uygulama dosyaları iletişim kutusunu** açmak Için **uygulama dosyaları** düğmesine tıklayın.

4. **Uygulama dosyaları** iletişim kutusunda yeni gruba dahil etmek istediğiniz bir dosya için **Grup** alanını seçin.

    > [!NOTE]
    > Dosya adları, **uygulama dosyaları** iletişim kutusunda görüntülenmeden önce dosyalar Için **derleme eylemi** özelliği **içeriğe** ayarlanmış olmalıdır.

5. **Yükleme grubu** alanında, **\<New...>** açılan listeden öğesini seçin.

6. **Yeni Grup** iletişim kutusunda Grup için bir ad girin ve ardından **Tamam**' a tıklayın.

### <a name="to-add-a-file-to-a-group"></a>Bir gruba dosya eklemek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Uygulama dosyaları iletişim kutusunu** açmak Için **uygulama dosyaları** düğmesine tıklayın.

4. **Uygulama dosyaları** iletişim kutusunda yeni gruba dahil etmek istediğiniz bir dosya için **Grup** alanını seçin.

5. **Yükleme grubu** alanında, açılan listeden bir grup seçin.

    > [!NOTE]
    > Uygulamanın çalışması için gerekli olan dosyalar için **Indirme grubunu** değiştiremezsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)