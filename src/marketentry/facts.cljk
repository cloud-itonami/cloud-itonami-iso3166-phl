(ns marketentry.facts "Philippines market-entry catalog.")
(def catalog
  {"PHL" {:name "Philippines"
          :owner-authority "GPPB / PhilGEPS"
          :legal-basis "RA 9184 Government Procurement Reform Act"
          :national-spec "PhilGEPS supplier registration + SEC/DTI number"
          :provenance "https://www.philgeps.gov.ph/"
          :required-evidence ["SEC/DTI registration record" "PhilGEPS registration record" "SEC extract" "Authorized-representative record"]
          :rep-owner-authority "contracting authorities / GPPB"
          :rep-legal-basis "Philippine legal entity registration typically required for PhilGEPS awards"
          :rep-provenance "https://www.philgeps.gov.ph/"
          :corporate-number-owner-authority "SEC / BIR"
          :corporate-number-legal-basis "SEC registration / TIN"
          :corporate-number-provenance "https://www.sec.gov.ph/"}
   "USA" {:name "United States" :owner-authority "GSA/SAM.gov" :legal-basis "FAR" :national-spec "SAM.gov" :provenance "https://sam.gov/"
          :required-evidence ["EIN record" "SAM.gov registration record" "State business registration record" "SAM UEI verification record"]}
   "IDN" {:name "Indonesia" :owner-authority "SPSE" :legal-basis "Perpres" :national-spec "SPSE" :provenance "https://lpse.lkpp.go.id/"
          :required-evidence ["NIB/NPWP record" "SPSE registration" "AHU extract" "Authorized-representative record"]}
   "SGP" {:name "Singapore" :owner-authority "GeBIZ" :legal-basis "GFR" :national-spec "GeBIZ" :provenance "https://www.gebiz.gov.sg/"
          :required-evidence ["UEN record" "GeBIZ registration" "GST record" "Authorized-representative record"]}})

(defn spec-basis [iso3] (get catalog iso3))
(defn coverage
  ([] (coverage (keys catalog)))
  ([iso3s]
   (let [have (filter catalog iso3s) missing (remove catalog iso3s)]
     {:requested (count iso3s) :covered (count have)
      :covered-jurisdictions (vec (sort have))
      :missing-jurisdictions (vec (sort missing))
      :note "R0 catalog seed"})))
(defn required-evidence-satisfied? [iso3 submitted]
  (when-let [{:keys [required-evidence]} (spec-basis iso3)]
    (= (count required-evidence) (count (filter (set submitted) required-evidence)))))
(defn evidence-checklist [iso3] (:required-evidence (spec-basis iso3) []))
(defn rep-spec-basis [iso3]
  (when-let [sb (spec-basis iso3)]
    (when (:rep-owner-authority sb)
      (select-keys sb [:rep-owner-authority :rep-legal-basis :rep-provenance]))))
(defn corporate-number-spec-basis [iso3]
  (when-let [sb (spec-basis iso3)]
    (when (:corporate-number-owner-authority sb)
      (select-keys sb [:corporate-number-owner-authority :corporate-number-legal-basis :corporate-number-provenance]))))
