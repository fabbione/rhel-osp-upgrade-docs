# Database upgrades

In general, if you have the `openstack-utils` package installed you
can use the `openstack-db` command to perform the below operations by
running:

    openstack-db --service <service> --update

For example:

    openstack-db --service keystone --update

This will run the database upgrade command appropriate for that
service.  For reference purposes, here are the actual commands that
will be run by `openstack-db`:

## Keystone

On the Keystone host, run:

    # keystone-manage db_sync

## Cinder

On the Cinder host, run:

    # cinder-manage db sync

## Swift

Swift does not require an explicit schema upgrade.

## Glance

On the Glance API host, run:

    # glance-manage db_sync

## Nova

On the Nova API host, run:

    # nova-manage db sync

## Neutron

On the Neutron host, run:

    # neutron-db-manage \
      --config-file /etc/neutron/neutron.conf \
      --config-file /etc/neutron/plugin.ini upgrade head

