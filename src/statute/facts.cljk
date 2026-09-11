(ns statute.facts
  "General-law compliance catalog for the Philippines (PHL) --
  extends this repo's existing `marketentry.facts` (narrow
  public-procurement scope) with a second, orthogonal catalog of
  statutes a company generally must track for compliance. Mirrors
  cloud-itonami-iso3166-jpn/-usa/-esp/-swe/-nor/-dnk/-fin/-prt/-bel/-bra/-mex/-chl/-arg/-zaf/-col/-ury/-cri/-pan/-ecu/-pry/-gtm/-hnd/-ind/-ken/-tha/-are/-vnm/-idn's
  `statute.facts` (ADR-2607141700, cloud-itonami-compliance-fact-federation).

  Reuses this tick-window's already-verified capital/organization data
  from cloud-itonami-municipality-phl-manila (Philippines Q928, Manila
  Q1461, capital status independently verified against the 1948-1976
  Quezon City interlude).

  Both entries directly confirmed via lawphil.net (a well-established
  Philippine legal database, the same source used successfully at
  tick 107 for Manila's Republic Act No. 409): Republic Act No. 11232
  (Revised Corporation Code of the Philippines) -- title/number
  confirmed on the page itself; the 20 February 2019 signing date
  (privacy.gov.ph returned HTTP 403, so this specific date is
  corroborated across multiple non-conflicting independent sources --
  ADB, Cruz Marcelo, AsiaLaw, IFLR, and the Official Gazette's own
  URL-embedded date -- rather than read directly off the lawphil.net
  page, which only gave the Congress session date). Republic Act No.
  10173 (Data Privacy Act of 2012) -- title, number, and 15 August
  2012 approval date all directly confirmed on the lawphil.net page
  itself.

  A law not in this table has NO spec-basis, full stop; extend
  `catalog`, do not invent an id/url.")

(def catalog
  "iso3 -> vector of statute entries."
  {"PHL"
   [{:statute/id "phl.ra-11232-revised-corporation-code"
     :statute/title "An Act Providing for the Revised Corporation Code of the Philippines"
     :statute/jurisdiction "PHL"
     :statute/kind :law
     :statute/law-number "Republic Act No. 11232"
     :statute/url "https://lawphil.net/statutes/repacts/ra2019/ra_11232_2019.html"
     :statute/url-provenance :lawphil-net-legal-database
     :statute/enacted-date "2019-02-20"
     :statute/retrieved-at "2026-07-16"
     :statute/topic #{:corporate-governance :incorporation}}
    {:statute/id "phl.ra-10173-data-privacy-act"
     :statute/title "Data Privacy Act of 2012"
     :statute/jurisdiction "PHL"
     :statute/kind :law
     :statute/law-number "Republic Act No. 10173"
     :statute/url "https://lawphil.net/statutes/repacts/ra2012/ra_10173_2012.html"
     :statute/url-provenance :lawphil-net-legal-database
     :statute/enacted-date "2012-08-15"
     :statute/retrieved-at "2026-07-16"
     :statute/topic #{:data-protection :privacy}}]})

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
      :note (str "cloud-itonami-iso3166-phl statute.facts Wave 0 (ADR-2607141700): "
                 (count (get catalog "PHL")) " PHL statutes seeded with "
                 "official lawphil.net citations. Extend "
                 "`statute.facts/catalog`, never fabricate a law-id or URL.")})))

(defn by-topic [iso3 topic]
  (filterv #(contains? (:statute/topic %) topic) (spec-basis iso3)))
