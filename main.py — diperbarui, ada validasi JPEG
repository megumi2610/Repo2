"""Make the AI judge happy — entry program.

Copies the bundled image (happy.jpg) to the output path as entry.png.
Standard library only, no network, fully deterministic: the same input
bytes are written on every run.
"""

import os
import sys


def main() -> int:
    here = os.path.dirname(os.path.abspath(__file__))
    src = os.path.join(here, "happy.jpg")
    with open(src, "rb") as f_in:
        data = f_in.read()
    # Guard against shipping the wrong file: the bundled image must be a JPEG.
    if not data.startswith(b"\xff\xd8\xff"):
        raise SystemExit("happy.jpg is not a JPEG image")
    out_dir = os.environ.get("MAKEFUN_OUTPUT_DIR", "/output")
    os.makedirs(out_dir, exist_ok=True)
    dst = os.path.join(out_dir, "entry.png")
    with open(dst, "wb") as f_out:
        f_out.write(data)
    print(f"wrote {dst} ({len(data)} bytes)")
    return 0


if __name__ == "__main__":
    sys.exit(main())
