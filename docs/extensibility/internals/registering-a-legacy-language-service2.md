---
title: Eski Dil Hizmeti2 kaydı | Microsoft Docs
description: Bu makalede, kaynaklarda kullanılabilen çeşitli dil hizmeti seçenekleri için kayıt defteri Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 649f4039baa6d899aaa560fbaa0712c3e905b5c8db0edb46d95c18e8f55d0312
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121275300"
---
# <a name="registering-a-legacy-language-service-2"></a>Eski dil hizmetini kaydetme 2
Aşağıdaki bölümlerde, 'de kullanılabilen çeşitli dil hizmeti seçenekleri için kayıt defteri girdilerinin listesi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sağlanmaktadır.

 Aşağıdaki kayıt defteri girdileri listesinde *VS Reg Root,* X.Y HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudioeşittir; burada \\ *X.Y* sürüm  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] numarasıdır.

## <a name="registry-entries-for-language-service-options"></a>Dil Hizmeti Seçenekleri için Kayıt Defteri Girişleri
 *VS Reg Root*\Languages\Language Services Dil \\ *Adı* anahtarı aşağıdaki değerleri içerebilir.

|Ad|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|(Varsayılan)|REG_SZ|*\<GUID>*|Dil hizmetinin GUID'si.|
|LangResID|REG_DWORD|0x0-0xffff|Dilin yerelleştirilmiş metin adı için dize kaynak tanımlayıcısı (ResID).|
|Paket|REG_SZ|*\<GUID>*|VSPackage GUID'si.|
|ShowCompletion|REG_DWORD|0-1|Seçenekler iletişim kutusundaki **Deyim tamamlama** **seçeneklerinin** etkin olup olmadığını belirtir.|
|ShowSmartIndent|REG_DWORD|0-1|Seçenekler iletişim kutusunda Akıllı girinti **seçeneğinin** etkin **olup** olmadığını belirtir.|
|RequestStockColors|REG_DWORD|0-1|Anahtar sözcükleri renklendirmek için özel veya varsayılan renklerin kullanıp kullanılmay olmadığını belirtir.|
|ShowHotURLs|REG_DWORD|0-1|Kullanıcının URL'lere tıkıp tıklayayıp tıklamaycazı belirtir.|
|Varsayılan olarak Hot OLMAYAN URL'ler|REG_DWORD|0-1|Seçenekler iletişim kutusundaki Tek **tıklamayla URL gezintisini etkinleştir** seçeneğinin ilk **ayarını** belirtir.|
|DefaultToInsertSpaces|REG_DWORD|0-1|Dil hizmetinin varsayılan sekme seçeneği olarak "boşluk ekle" olup olmadığını belirtir.|
|ShowDropdownBarOption|REG_DWORD|0-1|Gezinti çubuğunu gösteren veya **gizleyen** Seçenekler **iletişim kutusunda** Gezinti çubuğu seçeneğini etkinleştiren veya devre **dışı bırakan.**|
|Yalnızca Tek Kod Penceresi|REG_DWORD|0-1|Dil hizmetinin Pencere **menüsünde Yeni Pencere** seçeneğini **etkinleştiren** veya devre dışı bırakan.|
|EnableAdvancedMembersOption|REG_DWORD|0-1|Gelişmiş Üyeleri Gizle için Seçenekler **iletişim** kutusu ayarını etkinleştirir **veya devre dışı bırakır.**|
|Destek CF_HTML|REG_DWORD|0-1|Düzenleyicinin HTML verilerini kopyalamayı ve yapıştırarak olanaklı olup olmadığını belirtir.|
|EnableLineNumbersOption|REG_DWORD|0-1|Seçenekler iletişim kutusundaki **Satır numaraları** seçeneklerinin **bir** dil hizmeti için etkin olup olmadığını belirtir.|
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Özel alanlar gibi gelişmiş üyelerin tamamlanma listelerinde gizlenip gizlen olmadığını belirtir.|
|ShowBraceCompletion|REG_DWORD|0-1|Seçenekler iletişim kutusundaki **Küme ayracı** tamamlama **seçeneğinin etkin** olup olmadığını belirtir.|

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

## <a name="registry-entries-for-debugger-languages-options"></a>Hata Ayıklayıcı Dilleri Seçenekleri için Kayıt Defteri Girişleri
 *VS Reg Root*\Languages\Language Services Dil \\ *Adı*\Debugger Languages \\ *GUID*\ key aşağıdaki değerleri içerebilir.

|Ad|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|(Varsayılan)|REG_SZ|metin|Varsayılan değer, dilin adını belgeley için kullanılabilir. Bu anahtarın adı, \AD7Metrics\Expression Değerlendirici içinde karşılık gelen bir girdisi olan bir ifade *\<VS Reg Root>* değerlendiricinin GUID'dir.|

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

## <a name="registry-entries-for-editor-tools-options"></a>Düzenleyici Araçları Seçenekleri için Kayıt Defteri Girişleri
 Özellik sayfaları ve özellik düğümleri için EditorToolsOptions anahtarının altına kayıt defteri anahtarları ebilirsiniz. Bu anahtarlar ve değerleri, Seçenekler iletişim **kutusundaki** (Araçlar menüsünde) dil hizmetini yapılandırmak için kullanılan özellik sayfalarını tanımlamaktadır.  Aşağıdaki örnekte, *Sayfa Adı* bir özellik sayfasının adı, *Düğüm* Adı ise Seçenekler iletişim kutusundaki ağaçtaki düğümün **adıdır.** Sayfa girişi ve düğüm girişi ayrı ayrı belirtilmelidir.

|Ad|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|(Varsayılan)|REG_SZ|Resid|Bu seçenek sayfasının yerelleştirilmiş görünen adı. Ad değişmez metin veya # olabilir; `nnn` `nnn` burada, belirtilen VSPackage'ın uydu DLL'sinde bir dize kaynak kimliğidir.|
|Paket|REG_SZ|*Guıd*|Bu seçenekler sayfasını uygulayan VSPackage GUID'si.|
|Sayfa|REG_SZ|*Guıd*|yöntemini çağırarak VSPackage'dan istekte bulunarak özellik sayfasının <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> GUID'si. Bu kayıt defteri girişi yoksa, kayıt defteri anahtarı bir sayfayı değil bir düğümü açıklar.|

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

## <a name="registry-entries-for-file-name-extension-options"></a>Dosya Adı Uzantısı Seçenekleri için Kayıt Defteri Girişleri
 Dosya uzantısının girişi, ".myext" gibi öndeki dönemi içermesi gerekir.

|Ad|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|(Varsayılan)|REG_SZ|*Guıd*|Bu dosya adı uzantısı türü için varsayılan dil hizmeti için hizmet GUID'si.|

### <a name="example"></a>Örnek

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>Düzenleyici Seçenekleri için Kayıt Defteri Girişleri
 *VS Reg Kök*\Düzenleyiciler anahtarı aşağıdaki değerleri içerebilir:

|Ad|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|(Varsayılan)|REG_SZ|""|Kullanılmayan; belgeleri için buraya adını koyabilirsiniz.|
|DefaultToolboxTab|REG_SZ|""|Düzenleyici etkin olduğunda varsayılan olarak ayarlanacak araç kutusu sekmesinin adı.|
|DisplayName|REG_SZ|Resid|Birlikte Aç iletişim **kutusunda görüntülenmek** için ad. Ad, dize kaynak kimliği veya standart biçimde bir addır.|
|ExcludeDefTextEditor|REG_DWORD|0-1|Birlikte Aç **menü komutu** için kullanılır. Belirli bir dosya türü için kullanılabilir düzenleyiciler listesinde varsayılan metin düzenleyicisini listeley istemiyorsanız, bu değeri 1 olarak ayarlayın.|
|LinkedEditorGUID|REG_SZ|*\<GUID>*|Codepage desteğiyle bir dosya açabilirsiniz herhangi bir dil hizmeti için kullanılır. Örneğin, Birlikte Aç komutunu kullanarak .txt bir  dosya açsanız, kaynak kod düzenleyicisini kodlama ile ve kodlama olmadan kullanmak için seçenekler sağlanır.<br /><br /> Alt anahtar adı içinde belirtilen GUID, codepage düzenleyici fabrikasına göredir; Bu kayıt defteri girdisinde belirtilen bağlantılı GUID, normal düzenleyici fabrikasına yöneliktir. Bu girişin amacı, IDE'nin varsayılan düzenleyiciyi kullanarak bir dosya açması yoksa IDE'nin listede bir sonraki düzenleyiciyi kullanmayı denemesidir. Bu düzenleyici fabrikası temelde başarısız olan düzenleyici fabrikasıyla aynı olduğundan, bir sonraki düzenleyici codepage düzenleyici fabrikası değildir.|
|Paket|REG_SZ|*\<GUID>*|Görünen adın ResID'si için VSPackage GUID'si.|

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

## <a name="registry-entries-for-logical-view-options"></a>Mantıksal Görünüm Seçenekleri için Kayıt Defteri Girdileri
 VS *Reg Kök*\Düzenleyiciler Düzenleyicisi GUI \\ *>* \LogicalViews anahtarı aşağıdaki değerleri içerebilir.

|Ad|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|(Varsayılan)|REG_SZ||Kullanılmıyor.|
|*\<GUID>*|REG_SZ|""|Desteklenen mantıksal görünümlerin anahtarı. Bunların birçoğuna ihtiyacınız olduğu kadar sahip olabilir. Kayıt defteri girişinin adı, her zaman boş bir dize olan değer değil, önemli olandır.|

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

## <a name="registry-entries-for-editor-extension-options"></a>Düzenleyici Uzantısı Seçenekleri için Kayıt Defteri Girişleri
 *VS Reg Kök*\Düzenleyiciler Düzenleyicisi \\ *GUID*\Extensions anahtarı aşağıdaki değerleri içerebilir. Dosya adı uzantısı, baştaki dönemi dahil değildir.

|Ad|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|(Varsayılan)|REG_SZ||Kullanılmıyor.|
|*\<ext>*|REG_DWORD|0-0xffffffff|Uzantıların göreli önceliği. İki veya daha fazla dil aynı uzantıyı paylaşıyorsa, yüksek öncelikli dil seçilir.|

 Ayrıca, geçerli kullanıcının düzenleyici için varsayılan seçimi HKEY_Current_User\Software\Microsoft\VisualStudio \\ *X.Y*\Default Editors ext dizininde \\ *depolanır.* Seçilen dil hizmetinin GUID'si Özel girdisindedir. Bu, geçerli kullanıcı için önceliklidir.

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

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Yönetilen Paket Çerçevesi Dil Hizmeti Seçenekleri için Kayıt Defteri Girişleri
 Aşağıdaki kayıt defteri girdileri yönetilen paket çerçevesi (MPF) dil hizmeti sınıflarını özel olarak içerir. Bu kayıt defteri girişleri, çeşitli IntelliSense özellikleri ve diğer gelişmiş düzenleme özellikleri için dil hizmeti desteğini gösteriyor.

 Bu kayıt defteri girişlerine sınıfı üzerinden <xref:Microsoft.VisualStudio.Package.LanguagePreferences> erişilir.

|Ad|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|CodeSense|REG_DWORD|0-1|IntelliSense işlemleri desteği.|
|MatchBraces|REG_DWORD|0-1|Parantez, parantezler ve köşeli ayraç gibi eşleşen dil çiftleri için destek.|
|QuickInfo|REG_DWORD|0-1|IntelliSense hızlı bilgi işlemi için destek.|
|Showmatchingayracın|REG_DWORD|0-1|Durum çubuğunda eşleşen dil çiftinin görüntülenmesi için destek.|
|Matchbracesatşapka|REG_DWORD|0-1|Genellikle iki öğenin vurgulanması yoluyla, eşleşen dil çiftlerini görüntüleme desteği.|
|MaxErrorMessages|REG_DWORD|0-n|**Hata listesi** penceresinde görüntülenebilen en fazla hata sayısı.|
|CodeSenseDelay|REG_DWORD|0-n|Bir IntelliSense işlemi için arka plan ayrıştırması başlatmadan önce gecikme süresi (milisaniye).|
|EnableAsyncCompletion|REG_DWORD|0-1|Arka plan ayrıştırma desteği.|
|Enableyorum oluşturma|REG_DWORD|0-1|Seçili metin bloklarını açıklama eklemek için destek ve ayrıca seçili metnin yorum kaldırma desteğini de gerektirir.|
|EnableFormatSelection|REG_DWORD|0-1|Otomatik girintileme veya küme ayraçları konumunu ayarlama gibi biçimlendirme metni için destek.|
|Oto anahat oluşturma|REG_DWORD|0-1|Ana hat (daraltılabilen bölgeler) için destek.|
|Maxregion|REG_DWORD|0-n|Dosya başına en fazla gizli bölge sayısı.|

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
