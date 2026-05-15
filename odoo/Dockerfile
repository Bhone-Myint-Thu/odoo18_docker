FROM python:3.11-slim

RUN apt-get update && apt-get install -y \
    git gcc g++ \
    libpq-dev \
    libxml2-dev libxslt1-dev \
    libldap2-dev libsasl2-dev \
    libjpeg-dev zlib1g-dev \
    libffi-dev libssl-dev \
    nodejs npm \
    && rm -rf /var/lib/apt/lists/*

RUN useradd -m odoo

WORKDIR /opt

RUN git clone https://github.com/odoo/odoo --branch 18.0 --depth 1

WORKDIR /opt/odoo

# Install Odoo official dependencies
RUN pip install --no-cache-dir -r requirements.txt

USER odoo

EXPOSE 8069

CMD ["python3", "odoo-bin", "-c", "/etc/odoo/odoo.conf"]