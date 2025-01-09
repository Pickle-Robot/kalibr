# Docker containers
```bash
# Build the container
docker build -f Dockerfile -t fiducial_board_generator .

# Run the pdf generator directly. Ensure to mount the directory
docker run -it --rm -v .:/app fiducial_board_generator -h # Pass args to script here

# Example
docker run -it --rm -v .:/app fiducial_board_generator --nx 2 --ny 1 --tsize 0.16 --tspace 0.25 --ids '302' --border-bits 1 --add-caption --add-id-caption
```

# Installation
- Install latex base (required to generate captions): `sudo apt-get install texlive-base`
- Install the requirements in this directory:
```bash
pip install -r requirements.txt
```

# Examples
```bash
python kalibr_create_target_pdf --type apriltag --nx 1 --ny 4 --tsize 0.22 --tspace 0.3 --ids '200' --border-bits 1 --add-caption --add-id-caption --caption-text 'LEFT'
```
will generate a fiducial board where the fiducials are of size 0.22m, and tagspace ratio of 0.3 (i.e., tag space is 0.3 * 0.22 = 0.066 m).
