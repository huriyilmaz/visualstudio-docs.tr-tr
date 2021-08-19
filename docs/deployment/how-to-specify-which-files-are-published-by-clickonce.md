---
title: Yayımlayacak dosyaları belirtme (ClickOnce)
description: Dosyaları dışlama, dosyaları veri dosyaları veya önkoşullar olarak işaretleme ve bir uygulama için koşullu yükleme için ClickOnce öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: c6fbe8b1543fdff870a0a5557c313080acd390c8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146296"
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>Nasıl kullanılır: Uygulama tarafından hangi dosyaların yayım ClickOnce
Bir uygulamayı [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yayımlarken, proje içinde yer alan kod olmayan tüm dosyalar uygulamayla birlikte dağıtılır. Bazı durumlarda, belirli dosyaları yayımlamak istemeyebilirsiniz veya yayımlamanız gerekebilirsiniz ya da belirli dosyaları koşullara göre yüklemek istiyor olabilir. Visual Studio, dosyaları dışlama, dosyaları veri dosyaları veya önkoşullar olarak işaretleme ve koşullu yükleme için dosya grupları oluşturma özellikleri sağlar.

 Bir uygulamanın dosyaları, Uygulama Dosyaları iletişim kutusunda yönetilir; bu, Uygulama [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Tasarımcısı'nın **Yayımla Project erişilebilir.**  

 Başlangıçta , (Gerekli) adlı tek bir **dosya grubu vardır.** Ek dosya grupları oluşturabilir ve bu gruplara dosya atabilirsiniz. Uygulamanın çalışması **için gereken** dosyalar için İndirme Grubunu değiştiremezsiniz. Örneğin, uygulamanın veri .exe veya veri dosyası olarak işaretlenmiş dosyalar **(Gerekli) grubuna ait** olması gerekir.

 Bir dosyanın varsayılan yayımlama durumu değeri ile etiketlenir **(Otomatik)**. Örneğin, uygulamanın kullanıcı .exe yayımlama durumu varsayılan olarak **Dahil Edildi (Otomatik)** olur.

 Derleme Eylemi özelliği **İçerik olarak** ayarlanmış **dosyalar** uygulama dosyaları olarak belirlenmiştir ve varsayılan olarak dahil edildi olarak işaretlenir. Bunlar dahil olabilir, hariç tutularak veya veri dosyası olarak işaretlenir. Özel durumlar aşağıdaki gibidir:

- SQL Veritabanı (*.mdf* ve *.mdb*) dosyaları ve XML dosyaları gibi veri dosyaları varsayılan olarak veri dosyaları olarak işaretlenir.

- Başvuru eklerken derlemelere *(.dll* dosyaları) başvurular şu şekilde belirlenmiştir: Yereli Kopyala False **ise,** varsayılan olarak uygulama yüklenmeden önce GAC'de mevcut olması gereken bir önkoşul derlemesi ( Önkoşul **(Otomatik)**) olarak işaretlenir.  Yereli **Kopyala** **true** ise, derleme varsayılan olarak bir uygulama derlemesi ( Dahil **(Otomatik) )** olarak işaretlenir ve yükleme sırasında uygulama klasörüne kopyalanır. Uygulama Dosyaları iletişim kutusunda  *(.ocx* dosyası olarak) yalnızca Yalıtılmış özelliği True olarak ayarlanırsa bir COM başvurusu **görüntülenir.**  Varsayılan olarak, dahil edilir.

### <a name="to-add-files-to-the-application-files-dialog-box"></a>Uygulama Dosyaları iletişim kutusuna dosya eklemek için

1. içinde bir veri dosyası **Çözüm Gezgini.**

2. Bu Özellikler penceresi Derleme Eylemi **özelliğini İçerik** değeri **olarak** değiştirebilirsiniz.

### <a name="to-exclude-files-from-clickonce-publishing"></a>Dosyaları yayımlamanın dışında ClickOnce için

1. içinde bir proje **seçiliyken Çözüm Gezgini** menüsünde **Project'a** **tıklayın.**

2. Yayımla **sekmesine** tıklayın.

3. Uygulama **Dosyaları düğmesine** tıklayarak Uygulama Dosyaları **iletişim kutusunu** açın.

4. Uygulama **Dosyaları** iletişim kutusunda, dışlamak istediğiniz dosyayı seçin.

5. Yayımlama **Durumu alanında,** açılan **listeden** Dışla'yı seçin.

### <a name="to-mark-files-as-data-files"></a>Dosyaları veri dosyası olarak işaretlemek için

1. içinde bir proje **seçiliyken Çözüm Gezgini** menüsünde **Project'a** **tıklayın.**

2. Yayımla **sekmesine** tıklayın.

3. Uygulama **Dosyaları düğmesine** tıklayarak Uygulama Dosyaları **iletişim kutusunu** açın.

4. Uygulama **Dosyaları iletişim** kutusunda, veri olarak işaretlemek istediğiniz dosyayı seçin.

5. Yayımlama **Durumu alanında,** açılan **listeden Veri** Dosyası'yı seçin.

### <a name="to-mark-files-as-prerequisites"></a>Dosyaları önkoşul olarak işaretlemek için

1. içinde bir proje **seçiliyken Çözüm Gezgini** menüsünde **Project'a** **tıklayın.**

2. Yayımla **sekmesine** tıklayın.

3. Uygulama **Dosyaları düğmesine** tıklayarak Uygulama Dosyaları **iletişim kutusunu** açın.

4. Uygulama **Dosyaları iletişim kutusunda,** önkoşul *olarak işaretlemek istediğiniz uygulama* derlemesi (.dlldosyası) öğesini seçin. Uygulamanın listede görünmesi için uygulama derlemesi başvurusu olması gerektiğini unutmayın.

5. Yayımlama **Durumu alanında,** açılan listeden Önkoşul'ı seçin. 

### <a name="to-add-a-new-file-group"></a>Yeni bir dosya grubu eklemek için

1. içinde bir proje **seçiliyken Çözüm Gezgini** menüsünde **Project'a** **tıklayın.**

2. Yayımla **sekmesine** tıklayın.

3. Uygulama **Dosyaları düğmesine** tıklayarak Uygulama Dosyaları **iletişim kutusunu** açın.

4. Uygulama **Dosyaları iletişim** kutusunda, yeni **gruba** eklemek istediğiniz bir dosyanın Grup alanını seçin.

    > [!NOTE]
    > Dosya adlarının **Uygulama Dosyaları iletişim** kutusunda görünmesi **için** dosyalarda Derleme Eylemi özelliğinin İçerik **olarak ayarlanmış** olması gerekir.

5. Grubu **İndir alanında,** **\<New...>** açılan listeden öğesini seçin.

6. Yeni **Grup iletişim** kutusunda, grup için bir ad girin ve ardından Tamam'a **tıklayın.**

### <a name="to-add-a-file-to-a-group"></a>Gruba dosya eklemek için

1. içinde bir proje **seçiliyken Çözüm Gezgini** menüsünde **Project'a** **tıklayın.**

2. Yayımla **sekmesine** tıklayın.

3. Uygulama **Dosyaları düğmesine** tıklayarak Uygulama Dosyaları **iletişim kutusunu** açın.

4. Uygulama **Dosyaları iletişim** kutusunda, yeni **gruba** eklemek istediğiniz bir dosyanın Grup alanını seçin.

5. Grubu **İndir alanında,** açılan listeden bir grup seçin.

    > [!NOTE]
    > Uygulamanın çalışması **için gereken** dosyalar için İndirme Grubunu değiştiremezsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl ClickOnce: ClickOnce Sihirbazı'nı kullanarak bir uygulama yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)