(ns culture.facts
  "Country-level regional-culture catalog for the Philippines (PHL) -- national
  dishes, protected products, beverages, crafts, festivals and heritage
  sites, per ADR-2607171400 addendum 2 (cloud-itonami-municipality-
  culture-catalog Wave 1, in com-junkawasaki/root). Sibling namespace to
  `marketentry.facts` / `statute.facts` (ADR-2607141700); city-level
  counterparts live in the cloud-itonami-municipality-* repos.

  Catalog is keyed by UPPERCASE ISO3 (mirrors `statute.facts`); entries
  carry no :culture/municipality (that attribute is city-level only).

  Every entry cites a source URL that was actually fetched and read on
  :culture/retrieved-at -- never fabricated. Summaries state only what the
  cited source confirms. An item not in this table has NO spec-basis, full
  stop; extend `catalog`, do not invent an id/url.")

(def catalog
  "iso3 -> vector of culture entries."
  {"PHL"
   [{:culture/id "phl.dish.adobo"
     :culture/name "Philippine adobo"
     :culture/country "PHL"
     :culture/kind :dish
     :culture/summary "Often considered the unofficial national dish of the Philippines; the Spanish name was applied to an indigenous cooking method using vinegar that had developed independently in the archipelago."
     :culture/url "https://en.wikipedia.org/wiki/Philippine_adobo"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "phl.dish.sinigang"
     :culture/name "Sinigang"
     :culture/country "PHL"
     :culture/kind :dish
     :culture/summary "Filipino soup or stew characterized by its sour and savory taste, typically soured with tamarind and served with rice."
     :culture/url "https://en.wikipedia.org/wiki/Sinigang"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "phl.dish.lechon"
     :culture/name "Lechon"
     :culture/country "PHL"
     :culture/kind :dish
     :culture/summary "The Filipino lechon has pre-colonial origins and uses weaned pigs with native ingredients like lemongrass and tamarind, diverging from the Spanish suckling-pig tradition."
     :culture/url "https://en.wikipedia.org/wiki/Lechon"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "phl.dish.halo-halo"
     :culture/name "Halo-halo"
     :culture/country "PHL"
     :culture/kind :dish
     :culture/summary "Popular cold dessert in the Philippines made with crushed ice, evaporated or coconut milk, and flavorings such as ube jam, beans and fruits, often topped with ice cream."
     :culture/url "https://en.wikipedia.org/wiki/Halo-halo"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "phl.beverage.tuba"
     :culture/name "Tuba"
     :culture/name-local "Tubâ"
     :culture/country "PHL"
     :culture/kind :beverage
     :culture/summary "Traditional Filipino palm wine made from the naturally fermented nectar of various species of palm trees, with an alcohol content of about 2-4%."
     :culture/url "https://en.wikipedia.org/wiki/Tuba_(drink)"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "phl.craft.tnalak"
     :culture/name "T'nalak"
     :culture/country "PHL"
     :culture/kind :craft
     :culture/summary "Weaving tradition of the T'boli people of South Cotabato, in which women who receive designs through dreams weave resist-dyed abaca cloth on a backstrap loom."
     :culture/url "https://en.wikipedia.org/wiki/T%27nalak"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "phl.craft.barong-tagalog"
     :culture/name "Barong Tagalog"
     :culture/country "PHL"
     :culture/kind :craft
     :culture/summary "Embroidered long-sleeved formal shirt for men and a national dress of the Philippines, combining precolonial native Filipino and Spanish colonial clothing elements."
     :culture/url "https://en.wikipedia.org/wiki/Barong_Tagalog"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "phl.festival.sinulog-festival"
     :culture/name "Sinulog Festival"
     :culture/country "PHL"
     :culture/kind :festival
     :culture/summary "Annual Filipino cultural and religious festival held on the third Sunday of January in Cebu, honoring the Santo Nino (Holy Child Jesus) and marking the Philippines' embrace of Christianity."
     :culture/url "https://en.wikipedia.org/wiki/Sinulog_Festival"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "phl.heritage.rice-terraces-cordilleras"
     :culture/name "Rice Terraces of the Philippine Cordilleras"
     :culture/country "PHL"
     :culture/kind :heritage
     :culture/summary "Rice terraces built into the mountains of Ifugao, inscribed on the UNESCO World Heritage List in 1995 as the first property in the cultural landscape category."
     :culture/url "https://en.wikipedia.org/wiki/Rice_Terraces_of_the_Philippine_Cordilleras"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}]})

(defn spec-basis [iso3] (get catalog iso3))

(defn coverage
  ([] (coverage (keys catalog)))
  ([iso3s]
   (let [have (filter catalog iso3s)
         missing (remove catalog iso3s)]
     {:requested (count iso3s)
      :covered (count have)
      :covered-jurisdictions (vec (sort have))
      :missing-jurisdictions (vec (sort missing))
      :note (str "cloud-itonami-iso3166-phl culture catalog "
                 "(ADR-2607171400 addendum 2, Wave 1): " (count (get catalog "PHL"))
                 " PHL entries, each with a fetched-and-read citation. "
                 "Extend `culture.facts/catalog`, never fabricate an id/url.")})))

(defn by-kind [iso3 kind]
  (filterv #(= (:culture/kind %) kind) (spec-basis iso3)))
