---
title: Eski Dil Hizmeti Nin Kaydedilmesi2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d9d13f301f6c04c0f7b14cc8c685f08b072ef84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705881"
---
# <a name="registering-a-legacy-language-service"></a>Eski Dil Hizmeti Kaydetme
Aşağıdaki bölümlerde, 'de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]bulunan çeşitli dil hizmeti seçenekleri için kayıt defteri girişlerinin listeleri bulunmaktadır.

 Aşağıdaki kayıt defteri girişleri *listesinde, VS Reg Root,* \\ *X.Y'nin* [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sürüm numarası olduğu HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio*X.Y'ye*eşittir.

## <a name="registry-entries-for-language-service-options"></a>Dil Hizmeti Seçenekleri için Kayıt Defteri Girişleri
 *VS Reg Root*\Languages\Language Services\\Dil*Adı* anahtarı aşağıdaki değerleri içerebilir.

|Adı|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|(Varsayılan)|REG_SZ|*\<REHBER>*|Dil hizmetinin GUID.|
|LangResID|REG_DWORD|0x0-0xffff|Dilin yerelleştirilmiş metin adı için string kaynak tanımlayıcısı (ResID).|
|Paket|REG_SZ|*\<REHBER>*|VSPackage'In REHBERİ.|
|ShowCompletion|REG_DWORD|0-1|**Seçenekler** iletişim kutusundaki **Ekstre tamamlama** seçeneklerinin etkin olup olmadığını belirtir.|
|ShowSmartIndent|REG_DWORD|0-1|**Seçenekler** iletişim kutusunda **Akıllı** girintiyi seçme seçeneğinin etkin olup olmadığını belirtir.|
|RequestStockColors|REG_DWORD|0-1|Özel veya varsayılan renklerin anahtar kelimeleri renklendirmek için kullanılıp kullanılmayacağını belirtir.|
|ShowHotURLs|REG_DWORD|0-1|Kullanıcının URL'leri tıklatıp tıklatamayacağını belirtir.|
|Varsayılan olarak Sıcak Olmayan URL'ler|REG_DWORD|0-1|**Seçenekler** iletişim kutusunda tek **tıklamayla URL gezinme** seçeneğini etkinleştir'in ilk ayarını belirtir.|
|DefaultToInsertSpaces|REG_DWORD|0-1|Varsayılan sekme seçeneği olarak dil hizmetinin "boşluk ekleme" olup olmadığını belirtir.|
|ShowDropdownBarOption|REG_DWORD|0-1|**Gezinti** **çubuğunu** gösteren veya gizleyen **Seçenekler** iletişim kutusunda Gezinti çubuğu seçeneğini etkinleştirir veya devre dışı kaldırır.|
|Yalnızca Tek Kod Penceresi|REG_DWORD|0-1|Bir dil hizmeti için **Pencere** menüsündeki **Yeni Pencere** seçeneğini etkinleştirir veya devre dışı kılabilir.|
|Gelişmiş Üyeler Seçeneğini Etkinleştir|REG_DWORD|0-1|**Gelişmiş Üyeleri Gizle**için **Seçenekler** iletişim kutusu ayarını etkinleştirir veya devre dışı bırakırsa.|
|Destek CF_HTML|REG_DWORD|0-1|Düzenleyicinin HTML verilerinin kopyalanmasını ve yapıştırılmasını etkinleştirip etkinleştirmediğini belirtir.|
|EnableLineNumbersOption|REG_DWORD|0-1|Bir dil hizmeti için **Seçenekler** iletişim kutusundaki **Satır numaraları** seçeneklerinin etkin olup olmadığını belirtir.|
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Özel alanlar gibi gelişmiş üyelerin tamamlanma listelerinde gizlenip gizlenmediğini belirtir.|
|ShowBraceTamamlama|REG_DWORD|0-1|**Seçenekler** iletişim **kutusundaki Ayraç tamamlama** seçeneğinin etkin olup olmadığını belirtir.|

### <a name="example"></a>Örnek

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
        LangResID             = reg_dword:0x00000000
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}
        ShowCompletion        = reg_dword:0x00000001
        ShowSmartIndent       = reg_dword:0x00000001
        ShowDropdownBarOption = reg_dword:0x00000001
```

## <a name="registry-entries-for-debugger-languages-options"></a>Hata Ayıklama Dilleri Seçenekleri için Kayıt Defteri Girişleri
 *VS Reg Root*\Languages\Language Services\\Dil*Adı*\Hata Ayıklama Dilleri\\*GUID*\ tuşu aşağıdaki değerleri içerebilir.

|Adı|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|(Varsayılan)|REG_SZ|metin|Varsayılan değer, dilin adını belgelemek için kullanılabilir. Bu anahtarın * \<adı, VS Reg Root>* \AD7Metrics\Expression Evaluator'da karşılık gelen bir girişi olan bir ifade değerlendiricisinin GUID'sidir.|

### <a name="example"></a>Örnek

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        Debugger Languages\
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\
            (Default) = reg_sz:C++
```

## <a name="registry-entries-for-editor-tools-options"></a>Editör Araçları Seçenekleri için Kayıt Defteri Girişleri
 Özellik sayfaları ve özellik düğümleri için EditorToolsOptions anahtarının altına kayıt defteri anahtarları ekleyebilirsiniz. Bu anahtarlar ve değerleri, dil hizmetini yapılandırmak için kullanılan **Seçenekler** iletişim kutusundaki **(Araçlar** menüsünde) özellik sayfalarını tanımlar. Aşağıdaki örnekte, *Sayfa Adı* bir özellik sayfasının adıdır ve Düğüm *Adı,* **Seçenekler** iletişim kutusundaki ağaçtaki düğümün adıdır. Sayfa girişi ve düğüm girişi ayrı olarak belirtilmelidir.

|Adı|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|(Varsayılan)|REG_SZ|Resid|Bu seçenek sayfasının yerelleştirilmiş görüntü adı. Adı literal metin veya #`nnn`, `nnn` belirtilen VSPackage uydu DLL bir dize kaynak kimliği nerede olabilir.|
|Paket|REG_SZ|*Guıd*|Bu seçenekler sayfasını uygulayan VSPackage'ın GUID'i.|
|Sayfa|REG_SZ|*Guıd*|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> Yöntem çağırarak VSPackage'dan talep etmek için özellik sayfasının GUID. Bu kayıt defteri girişi yoksa, kayıt defteri anahtarı sayfa yı değil, bir düğüm açıklar.|

### <a name="example"></a>Örnek

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      CSharp\
        EditorToolsOptions\
          Formatting\
            (Default) = reg_sz:#242
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
            General\
              (Default) = reg_sz:#255
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}
            Indentation\
              (Default) = reg_sz:#250
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}
            Newlines\
              (Default) = reg_sz:#253
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}
```

## <a name="registry-entries-for-file-name-extension-options"></a>Dosya Adı Uzatma Seçenekleri için Kayıt Defteri Girişleri
 Dosya uzantısı girişi, örneğin ".myext" gibi satır aralığını içermelidir.

|Adı|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|(Varsayılan)|REG_SZ|*Guıd*|Bu dosya adı uzantısı türü için varsayılan dil hizmeti için Hizmet GUID.|

### <a name="example"></a>Örnek

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>Editör Seçenekleri için Kayıt Defteri Girişleri
 *VS Reg Root*\Editors tuşu aşağıdaki değerleri içerebilir:

|Adı|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|(Varsayılan)|REG_SZ|""|Kullanılmayan; dokümantasyon için adınızı buraya koyabilirsiniz.|
|VarsayılanAraç Kutusu Sekmesi|REG_SZ|""|Düzenleyici etkinolduğunda varsayılan yapmak için araç kutusu sekmesinin adı.|
|DisplayName|REG_SZ|Resid|**İletişim kutusuyla aç** kutusunda görüntülenecek ad. Ad, dize kaynak kimliği veya standart biçimdeki bir addır.|
|ExcludeDefTextEditor|REG_DWORD|0-1|**Menü ile aç** komutu için kullanılır. Varsayılan metin düzenleyicisini belirli bir dosya türü için kullanılabilir düzenleyiciler listesinde listelemek istemiyorsanız, bu değeri 1 olarak ayarlayın.|
|LinkedEditorGUID|REG_SZ|*\<REHBER>*|Kod sayfası desteği olan bir dosyayı açabilen herhangi bir dil hizmeti için kullanılır. Örneğin, .txt dosyasını **"Ile Aç"** komutunu kullanarak açtığınızda, kaynak kod düzenleyicisini kodlamadan ve kodlamadan kullanmak için seçenekler sağlanır.<br /><br /> Alt anahtar adında belirtilen GUID codepage düzenleyici fabrikası içindir; bu özel kayıt defteri girişinde belirtilen bağlantılı GUID normal düzenleyici fabrikası içindir. Bu girişin amacı, IDE varsayılan düzenleyiciyi kullanarak bir dosyayı açmazsa, IDE'nin listedeki bir sonraki düzenleyiciyi kullanmayı deneyeceğidir. Bu editör fabrikası temelde başarısız editör fabrikası ile aynı olduğundan, bu sonraki düzenleyici kod düzenleyicisi fabrikası olmamalıdır.|
|Paket|REG_SZ|*\<REHBER>*|Görüntü adının ResID'si için VSPackage GUID.|

### <a name="example"></a>Örnek

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      (Default)            = reg_sz:Html Editor with Encoding
      DefaultToolboxTab    = reg_sz:HTML
      DisplayName          = reg_sz:#20101
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}
```

## <a name="registry-entries-for-logical-view-options"></a>Mantıksal Görünüm Seçenekleri için Kayıt Defteri Girişleri
 *VS Reg Root*\Editors\\*EditorGUI>* \LogicalViews tuşu aşağıdaki değerleri içerebilir.

|Adı|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|(Varsayılan)|REG_SZ||Kullanılmıyor.|
|*\<REHBER>*|REG_SZ|""|Desteklenen mantıksal görünümlerin anahtarı. İhtiyacınız olduğu kadar çok tane alabilirsiniz. Kayıt defteri girişinin adı, her zaman boş bir dize olan değer değil, önemli olandır.|

### <a name="example"></a>Örnek

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      LogicalViews\
       (Default) = reg_sz:
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
```

## <a name="registry-entries-for-editor-extension-options"></a>Düzenleyici Uzatma Seçenekleri için Kayıt Defteri Girişleri
 *VS Reg Root*\Editors\\Editor*GUID*\Extensions tuşu aşağıdaki değerleri içerebilir. Dosya adı uzantısı satır aralığını içermez.

|Adı|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|(Varsayılan)|REG_SZ||Kullanılmıyor.|
|*\<ext>*|REG_DWORD|0-0xffffffff|Uzantıların göreli önceliği. İki veya daha fazla dil aynı uzantıyı paylaşıyorsa, daha yüksek öncelikli dil seçilir.|

 Ayrıca, bir düzenleyici için geçerli kullanıcının varsayılan seçimi\\HKEY_Current_User\Software\Microsoft\VisualStudio*X.Y*\Default Editors\\*ext*depolanır. Seçilen dil hizmetinin GUID'i Özel giriştedir. Bu, geçerli kullanıcı için önceliklidir.

### <a name="example"></a>Örnek

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      Extensions\
       (Default) = reg_sz:
       *         = reg_dword:0x00000018
       html      = reg_dword:0x00000027
       shtm      = reg_dword:0x00000027
       shtml     = reg_dword:0x00000027
```

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Yönetilen Paket Çerçeve Dil Hizmeti Seçenekleri için Kayıt Defteri Girişleri
 Aşağıdaki kayıt defteri girişleri yönetilen paket çerçevesi (MPF) dil hizmeti sınıflarına özgür. Bu kayıt defteri girişleri, çeşitli IntelliSense özellikleri ve diğer gelişmiş düzenleme özellikleri için dil hizmetinde destek gösterir.

 Bu kayıt defteri girişlerine <xref:Microsoft.VisualStudio.Package.LanguagePreferences> sınıf aracılığıyla erişilir.

|Adı|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|CodeSense|REG_DWORD|0-1|IntelliSense işlemleri için destek.|
|Eşleştirme Ayraçları|REG_DWORD|0-1|Ayraçlar, parantezler ve parantezler gibi eşleşen dil çiftleri için destek.|
|QuickInfo|REG_DWORD|0-1|IntelliSense Hızlı Bilgi işlemi için destek.|
|ShowMatchingBrace|REG_DWORD|0-1|Durum çubuğunda eşleşen dil çiftini görüntülemek için destek.|
|MatchBracesAtCaret|REG_DWORD|0-1|Genellikle iki öğeyi vurgulayarak eşleşen dil çiftleri görüntüleme desteği.|
|MaxErrorMesajlar|REG_DWORD|0-n|**Hata Listesi** penceresinde görüntülenebilen maksimum hata sayısı.|
|CodeSenseDelay|REG_DWORD|0-n|IntelliSense işlemi için herhangi bir arka plan ayrıştırma başlatmadan önce geciktirecek milisaniye sayısı.|
|EtkinleştirEAsyncCompletion|REG_DWORD|0-1|Arka plan ayrıştma desteği.|
|Yorumu Etkinleştirme|REG_DWORD|0-1|Seçili metin bloklarını açıklama desteği ve ayrıca seçili metnin yorumsuz kısıtımı için destek anlamına gelir.|
|Format Seçimini Etkinleştir|REG_DWORD|0-1|Otomatik girinti veya ayraçların konumunu ayarlama gibi metni biçimlendirme desteği.|
|Otomatik Özetleme|REG_DWORD|0-1|Anahat oluşturma desteği (daraltılabilir bölgeler).|
|MaxRegions|REG_DWORD|0-n|Dosya başına en fazla gizli bölge sayısı.|

```
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      XML\
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}
        MatchBraces           = reg_dword:0x00000001
        QuickInfo             = reg_dword:0x00000001
        ShowMatchingBrace     = reg_dword:0x00000001
        MatchBracesAtCaret    = reg_dword:0x00000000
        MaxErrorMessages      = reg_dword:0x00000064
        CodeSenseDelay        = reg_dword:0x000001f4
        MaxRegions            = reg_dword:0x0000000a
```

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)
