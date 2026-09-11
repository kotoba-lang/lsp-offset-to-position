(ns kotoba.lsp.offset-to-position
  "offset->position -- addressed on its own.

  Split out of kotoba.lang.lsp on 2026-09-09 (ADR-2609091200). The unit
  here is the DEFINITION, and this repo's deps.edn names exactly the
  definitions it reaches -- nothing else.
"
  )

(defn offset->position
  "Convert a character offset to a position."
  [doc offset]
  (let [starts (:line-starts doc)
        ;; largest line whose start is <= offset (linear — line counts are small)
        line (loop [l 0]
               (if (and (< (inc l) (count starts))
                        (<= (nth starts (inc l)) offset))
                 (recur (inc l))
                 l))]
    {:line line :character (- offset (nth starts line))}))
