# Fon Krizi Çözüm Senaryoları

**2026 fon tasfiyesi için geri kazanım ve kayıp dağılımı modeli**

SPK'nın 17 Eylül 2026 tarihli ve 2026/60 sayılı bülteniyle tasfiyesine karar verilen, 7 portföy yönetim şirketine ait 131 fonun yatırımcılarına ne kadar, ne zaman ve hangi sırayla geri ödeme yapılabileceğini hesaplayan açık bir model.

**Canlı sürüm:** `https://<kullanıcı-adınız>.github.io/fon-krizi-cozum-senaryolari/`
**Rapor (PDF):** [docs/fon-krizi-cozum-senaryolari-rapor-v1.0.pdf](docs/fon-krizi-cozum-senaryolari-rapor-v1.0.pdf)

## Ne soruyor?

Tasfiyedeki fonların 16.09.2026 itibarıyla net değeri 842,7 milyar TL. Bu varlığın %57'si hisse senedi, %20,5'i ters repo alacağı ve hisselerin önemli kısmı, fonların halka açık payın yarısından fazlasını tuttuğu sığ şirketlerde. Model üç soruya ve bir ek soruya yanıt arıyor:

1. **Ne kadar?** Portföy nakde çevrildiğinde 16.09 değerinin yüzde kaçı yatırımcıya döner?
2. **Ne zaman?** Ödemeler hangi takvimle gelir, paranın zaman değeri düşülünce ne kalır?
3. **Hangi sırayla?** Fonlar kapatılmasaydı ilk çıkanlarla sona kalanlar arasında kayıp nasıl dağılırdı?
4. **Kamu öderse?** Anaparanın altında kalan kayıp kamu tarafından karşılansaydı tutarı ne olurdu ve hangi kaynaklardan nasıl finanse edilirdi?

## Varsayılan ayarlarla temel bulgular

| | |
|---|---|
| Tasfiyede nominal geri dönüş (6 aylık azami süre içinde kademeli satış) | %66,5 |
| Aynı senaryonun bugünkü değeri | %59,5 |
| Satış yöntemi ve süreye göre aralık (dış destek hariç) | %62,5 – %69,3 |
| Fonlar açık kalsaydı: ilk çıkan %25 / sona kalan %25 | %100 / %0 |
| Anaparanın kamu tarafından karşılanması: net kamu yükü (tam nominal anapara, halefiyet sonrası) | 127 mlr TL (GSYH'nin %0,16'sı; 2026 bütçe açığı hedefinin %4,7'si) |
| Aynı yük, geri dönüş %15 olsaydı | 509 mlr TL (açık hedefinin %19'u) |
| Ters reponun güvencesi (TP2): DİBS teminatı | yalnızca %22 |

Toplam geri dönüşü büyük ölçüde sığ hisselerin gerçek değeri belirliyor; politika seçimi asıl olarak kaybın nasıl paylaşılacağını belirliyor. Tüm sonuçlar varsayımlara bağlıdır.

## Bileşenler

- **Senaryo simülatörü:** altı satış yöntemi (hızlı zorunlu satış, süre uzatımı, blok satış, ayni dağıtım, kurumsal alım tabanı, hibrit), şelale grafiği, ödeme takvimi, kohort analizi.
- **Tasfiye olmasaydı:** günlük iade, satış, taban kilidi ve temerrüt motoru; yedi alternatif yol (müdahale yok, iade kotası, adil fiyattan iade, geçici durdurma, yan cep, ayni iade ve gerçekleşen tasfiye).
- **Kamu tazmini:** anaparanın altında kalan kaybın kamu tarafından ödenmesi halinde tutarı (nominal veya enflasyonlu anapara, tavan, kısmi koruma, dönem kesiti) ve net yükün borçlanma, bütçe içi tasarruf, sektör katkısı, kamu kuruluşları ve ek vergi arasındaki dağılımı; 2026 bütçe ölçeğiyle karşılaştırma ve geri dönüş oranına duyarlılık. Resmî bir tazmin kararı yoktur; sekme bir politika önerisi değil, hesap aracıdır.
- **Yatırımcı hesabı:** adet, fiyat ve maliyetle kişisel tahmini ödeme ve takvim.
- **Kriz verisi:** varlık dağılımı, şirket ve fon tabloları, kronoloji.
- **Veri defteri:** modeldeki her sayı *Veri / Türetilmiş / Vekil / Varsayım* olarak etiketli; her satırda açığı hangi verinin kapatacağı yazıyor.

## Çalıştırma

Tek dosyadır, kurulum gerekmez. `index.html` dosyasını tarayıcıda açın. Tüm hesaplar tarayıcıda yapılır; hiçbir veri dışarı gönderilmez. Ayarlar yalnızca sizin tarayıcınızda saklanır.

## Veri kaynakları

- TEFAS 16.09.2026 fon büyüklükleri ve portföy dağılımları
- KAP portföy dağılım raporları, 31.08.2026 (TP2, TLY, PRY)
- SPK bültenleri (2026/60, 2026/61, 2026/62), 20.09.2026 süre düzenlemesi ve 28.09.2026 basın duyurusu
- TSPB, QNB Invest, CNBC-e ve diğer basın kaynakları (tam liste uygulamanın "Yöntem ve kaynaklar" sekmesinde ve raporda)

## Katkı ve tartışma

Model bilinçli olarak eksiklikleriyle yayımlanıyor. Özellikle şu konularda katkı arıyoruz:

- 16.09 sonrası hisse kapanışları ve hisse bazında işlem hacmi (erime süresi ve fiyat etkisi kalibrasyonu)
- TP2 dışındaki fonların ters repo teminat dökümleri
- Karşı tarafın nakit ödeme gücü ve TPKGY teminatının değeri
- Tasfiyede blok satış, yan cep ve ayni dağıtımın mevzuata uygunluğu
- Hesaplama hataları

Veri düzeltmesi için bir **Issue** açın (şablon hazır), fikir tartışması için **Discussions** bölümünü kullanın. Lütfen her veri önerisine kaynağını ekleyin.

## Sınırlar

- 16.09 tarihli teminat listesi yerine 31.08 raporları kullanılıyor.
- Ters reponun %14'ü için vekil fon dökümü kullanılıyor.
- Fonlar arası çapraz paylar konsolide edilmiyor (toplam en az 12,5 milyar TL şişik).
- Vergi etkisi hesaba katılmıyor.
- Kamu tazmini sekmesinde yatırımcı bazında maliyet ve pozisyon verisi yok; kohort dağılımı örnek, pozisyon dağılımı log-normal varsayımdır. Borçlanma, vergi ve harcama kısıtının makro etkileri modellenmez.

## Yasal uyarı

Bu çalışma, kamuya açık verilerle hazırlanmış bağımsız bir analiz ve eğitim amaçlı simülasyondur. 6362 sayılı Sermaye Piyasası Kanunu kapsamında yatırım danışmanlığı değildir; hiçbir finansal aracın alımı, satımı veya elde tutulması için öneri niteliği taşımaz. Ödemelerin tutarını ve zamanını yalnızca tasfiye yetkilisi kuruluşlar belirler. Veriler doğruluk garantisi olmaksızın sunulur. Adı geçen kurum ve kişilere ilişkin gözlem ve çıkarımlar teyit bekleyen analitik değerlendirmelerdir, suç isnadı içermez; devam eden soruşturmalarda masumiyet karinesi esastır. Çalışmanın SPK, Takasbank, MKK, tasfiye yetkilisi bankalar veya adı geçen şirketlerle bağlantısı yoktur.

## Lisans ve künye

© 2026 ARC Studios, Emre Arıcı

- Kaynak kodu: [MIT Lisansı](LICENSE)
- Rapor ve metinler: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.tr) (kaynak göstererek paylaşılabilir)

Alıntılarda: *Arıcı, E. (2026). Fon Krizi Çözüm Senaryoları: 2026 fon tasfiyesi için geri kazanım ve kayıp dağılımı modeli, Sürüm 1.0. ARC Studios.*
